# [Location](https://developer.android.com/training/location/retrieve-current)

A definite strength / added benefit of today's technology is the ability to ping numerous sensors that are ubiquitous in modern handsets, location being relevant, and simple to utilize if so desired.

Android clearly lays out the groundwork in order to obtain the location data from the gps sensor (or perhaps by means of cellphone tower if gps isn't available), and can be found [here](https://developer.android.com/training/location/retrieve-current) (and all code snippets are from that link unless otherwise noted).

Because location's services, you will need to inncorporate various services in the manifest, which is different depending on the use of location data and api level of the phone, as noted in the below [code snippet](https://developer.android.com/training/location/permissions):
``` Java
<!-- Recommended for Android 9 (API level 28) and lower. -->
<!-- Required for Android 10 (API level 29) and higher. -->
<service
    android:name="MyNavigationService"
    android:foregroundServiceType="location" ... >
    <!-- Any inner elements would go here. -->
</service>
// AS WELL AS:
<manifest ... >
  <!-- To request foreground location access, declare one of these permissions. -->
  <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
</manifest>
// And if the app only uses location data in the background:
<manifest ... >
  <!-- Required only when requesting background location access on
       Android 10 (API level 29) and higher. -->
  <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />
</manifest>
```

There is also an important detour into ensuring that you properly communicate to the user that the app will use the phone's location data, and those details can be seen [here](https://developer.android.com/training/permissions/requesting).

Then, the app's ```onCreate()``` needs the following code:
``` Java
private FusedLocationProviderClient fusedLocationClient;

// ..

@Override
protected void onCreate(Bundle savedInstanceState) {
    // ...

    fusedLocationClient = LocationServices.getFusedLocationProviderClient(this);
}
```
at which point the groundwork is set, and the basic means to get the most recent location data is by calling ```getLastLocation()```, and that basic code block looks like so:
``` Java
fusedLocationClient.getLastLocation()
        .addOnSuccessListener(this, new OnSuccessListener<Location>() {
            @Override
            public void onSuccess(Location location) {
                // Got last known location. In some rare situations this can be null.
                if (location != null) {
                    // Logic to handle location object
                }
            }
        });
```

Likely due to many extant factors (satellite coverage, obstruction to satellites, general potential flakiness of phones) the documentation suggests incorporating logic in order to best assess if the latest location is in fact reliable.
