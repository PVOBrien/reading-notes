# Room

## [An Overview](https://developer.android.com/training/data-storage/room)

> "Room provides an abstraction layer over SQLite to allow fluent database access while harnessing the full power of SQLite."
(above quote from [here](https://developer.android.com/training/data-storage/room))

When you need a non-trivial amount of content to be accessible offline, Android recommends Room! (Sounds like an advert!) It does seem there are reasons for this - persistence, the ease to upload the data online when possible, and abstraction (which I assume allows for higher level of security).

## 3 Major Components in Room

### - Database: the hub for the data to connect to other points.
### - Entity: a table.
### - DAO - AKA Data Access Objects, "contains the methods used for accessing the database."

## [Data Definition in Room](https://developer.android.com/training/data-storage/room/defining-data)
Note: the following code blocks are originally from [here](https://developer.android.com/training/data-storage/room/defining-data).

How to Define an Entity:

``` Java
@Entity
public class User {
    @PrimaryKey
    public int id;

    public String firstName;
    public String lastName;
}
```
and don't forget your getters, setters, and a standard constructor.
Of note: table names in Room/SQLite are case-insensitive.
Also: using @Ignore annotation allows/makes it so that field/column will not persist. I'm currently uncertain why you would create a column for something that you don't want to be stored there, but there must be reasons.

Lastly, ```@AutoValue``` and ```@CopyAnnotations``` seems to be a very useful tool, but I can't quite parse it just yet what it does.

## [Defining Relationships Between Objects](https://developer.android.com/training/data-storage/room/relationships)
Note: the following code blocks are originally from [here](https://developer.android.com/training/data-storage/room/relationships).
How to wire it all up, so that tables are related to other tables. There are the one-to-one, one-to-many, many-to-one, and many-to-many relationships.

- One-to-One:

``` Java
public class UserAndLibrary {
    @Embedded public User user;
    @Relation(
         parentColumn = "userId", // this column exists in another entity
         entityColumn = "userOwnerId" // this column exists in another entity
    )
    public Library library;
}
```

and how to to access the results:

``` Java
@Transaction
@Query("SELECT * FROM User")
public List<UserAndLibrary> getUsersAndLibraries();
```

- One-to-Many / Many-to-One

``` Java
@Entity
public class User {
    @PrimaryKey public long userId;
    public String name;
    public int age;
}

@Entity
public class Playlist {
    @PrimaryKey public long playlistId;
    public long userCreatorId;
    public String playlistName;
}

// Setup the tables above ^^^
// Then below link them accordingly

public class UserWithPlaylists {
    @Embedded public User user;
    @Relation(
         parentColumn = "userId",
         entityColumn = "userCreatorId"
    )
    public List<Playlist> playlists;
}

// And query like:

@Transaction
@Query("SELECT * FROM User")
public List<UserWithPlaylists> getUsersWithPlaylists();
```

- Many-to-Many

``` Java
// First setup the tables/Entities

@Entity
public class Playlist {
    @PrimaryKey public long playlistId;
    public String playlistName;
}

@Entity
public class Song {
    @PrimaryKey public long songId;
    public String songName;
    public String artist;
}

@Entity(primaryKeys = {"playlistId", "songId"})
public class PlaylistSongCrossRef {
    public long playlistId;
    public long songId;
}

// Think through how you want to access the tables, and keep onto that thought.

public class PlaylistWithSongs {
    @Embedded public Playlist playlist;
    @Relation(
         parentColumn = "playlistId",
         entityColumn = "songId",
         associateBy = @Junction(PlaylistSongCrossref.class)
    )
    public List<Song> songs;
}

public class SongWithPlaylists {
    @Embedded public Song song;
    @Relation(
         parentColumn = "songId",
         entityColumn = "playlistId",
         associateBy = @Junction(PlaylistSongCrossref.class)
    )
    public List<Playlist> playlists;
}

// And here is how to query the results

@Transaction
@Query("SELECT * FROM Playlist")
public List<PlaylistWithSongs> getPlaylistsWithSongs();

@Transaction
@Query("SELECT * FROM Song")
public List<SongWithPlaylists> getSongsWithPlaylists();
```

There is also space to allow for "nested relationships" to have even greater control and nuance over what can be linked together and more easily utilized as such:

``` Java

// Setting up the tables and their relationships

@Entity
public class User {
    @PrimaryKey public long userId;
    public String name;
    public int age;
}

@Entity
public class Playlist {
    @PrimaryKey public long playlistId;
    public long userCreatorId;
    public String playlistName;
}
@Entity
public class Song {
    @PrimaryKey public long songId;
    public String songName;
    public String artist;
}

@Entity(primaryKeys = {"playlistId", "songId"})
public class PlaylistSongCrossRef {
    public long playlistId;
    public long songId;
}

// Connect two of the tables as usual...

public class PlaylistWithSongs {
    @Embedded public Playlist playlist;
    @Relation(
         parentColumn = "playlistId",
         entityColumn = "songId",
         associateBy = @Junction(PlaylistSongCrossRef.class)
    )
    public List<Song> songs;
}

// Then, create *another* data class in order to nest them. (?)

public class UserWithPlaylistsAndSongs {
    @Embedded public User user;
    @Relation(
        entity = Playlist.class,
        parentColumn = "userId",
        entityColumn = "userCreatorId"
    )
    public List<PlaylistWithSongs> playlists;
}

// So it looks like this https://developer.android.com/images/training/data-storage/room_nested_relationships.png

// Now you can have results per this query:

@Transaction
@Query("SELECT * FROM User")
public List<UserWithPlaylistsAndSongs> getUsersWithPlaylistsAndSongs();

// NOTE: documentation states this is data intensive and can impact performance.
```

- [Accessing Data using Room DAOs](https://developer.android.com/training/data-storage/room/accessing-data#java) <br>
Note: the following code blocks are originally from [here](https://developer.android.com/training/data-storage/room/accessing-data#java). <br>

DAOs - Data Access Objects - are the means to access an app's data using Room, and this approach allows for "seperation of different components of your database architecture", and be either an interface or an abstract, and there are methods available for convenience:

``` Java

// Insert

@Dao
public interface MyDao {
    @Insert(onConflict = OnConflictStrategy.REPLACE)
    public void insertUsers(User... users);

    @Insert
    public void insertBothUsers(User user1, User user2);

    @Insert
    public void insertUsersAndFriends(User user, List<User> friends);
}

// Update

@Dao
public interface MyDao {
    @Update
    public void updateUsers(User... users);
}

// Delete

@Dao
public interface MyDao {
    @Delete
    public void deleteUsers(User... users);
}
```

- @Query

Data can be queried (as tables should be).

``` Java

// a simple query

@Dao
public interface MyDao {
    @Query("SELECT * FROM user")
    public User[] loadAllUsers();
}

// one with additional parameters:

@Dao
public interface MyDao {
    @Query("SELECT * FROM user WHERE age > :minAge")
    public User[] loadAllUsersOlderThan(int minAge);
}

// ... many more ways to query ...

// How to paginate results:

@Dao
interface UserDao {
  @Query("SELECT * FROM users WHERE label LIKE :query")
  PagingSource<Integer, User> pagingSource(String query);
}

// Additional Resources if using Kotlin...

```

And so concludes an overview of a method for data persistence on Android using Room (that uses SQLite).
