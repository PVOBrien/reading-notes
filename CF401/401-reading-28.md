# [RecyclerView](https://developer.android.com/guide/topics/ui/layout/recyclerview#java)

## Overview

"More advanced and flexible version of ListView." The user interface container is ```RecyclerView```, and is filled with views by a _layout manager_ which can be a standard manager (e.g. ```LinearLayoutManager``` or ```GridLayoutManager```) or your own.

> "The views are represented by _view holder_ objects." And these objects are instances of a class defined by extending ```RecyclerView.ViewHolder```, and each view is responsible for displaying a single item (with a view).

```RecyclerView``` only creates as many view holders as needed, to be on screen at that time (and no longer).

> "The view holder objects are managed by an _adapter_, which you create by extending ```RecyclerView.Adapter```." This creates view holders as needed to be onscreen, binding the relevant data to it, "by assigning the viewholder to a position, calling the adapter's ```onBindViewHolder()```.

The rest of the article gets into the nuts and bolts to customize and tailor the RecycleView to specific needs, wherein if you need to build it, it's best to go to it to read the details that are relevant for your purposes.
