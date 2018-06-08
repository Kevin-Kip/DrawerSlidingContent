## DrawerSlidingContent
Implementing android navigation drawer where the content moves, instead of the drawer overlaying the content.

## The magic
All you need is the following code

```java
DrawerLayout drawer = findViewById(R.id.drawer_layout);
ActionBarDrawerToggle toggle = new ActionBarDrawerToggle(
    this, drawer, toolbar, R.string.navigation_drawer_open, R.string.navigation_drawer_close){
    @Override
    public void onDrawerSlide(View drawerView, float slideOffset) {

    //this where the magic happens

         super.onDrawerSlide(drawerView, slideOffset);
            float slideX = drawerView.getWidth() * slideOffset;
            mainPanel.setTranslationX(slideX);
            }
        };
drawer.setDrawerElevation(0f);//this removes the overlay shadow at the end of the drawer
drawer.setScrimColor(Color.TRANSPARENT);//this removes the dark overlay on content when drawer is open
drawer.addDrawerListener(toggle);
toggle.syncState();
```