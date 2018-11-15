# Utility

1. Custom Dialog in DialogMain.java and dialog.xml
2. Custom Snackbar with buttons and image in SnackbarMain.java and SnackbarMain.xml
3. BottomSheet
4. Top navigation bar
5. Tab view with view pager
6. Bottom navigation bar
7. Bottom bar with fab in center
8. WaveLoadingView with circular and rectangle view(full screen) in WaveloadingMain.java and WaveloadingMain.xml
          
9. FiftyShadesOf
          compile 'com.github.florent37:fiftyshadesof:1.0.0'
          
          FiftyShadesOf.with(context)
             .on(R.id.view1, R.id.view2, R.id.view3) //views id
             .on(view1, view2, view3) //views references 
             .on(viewGroup) //group of views
             .except(view1, view2) //skip a view
             .start();

10. Collapsing Toolbar 

          CollapsingToolbar.xml
          
          <android.support.design.widget.CoordinatorLayout
              android:layout_width="match_parent"
              android:layout_height="match_parent">

              <!-- Scrollable view here -->

            <com.google.android.material.appbar.AppBarLayout
                  android:id="+@id/appbar"
                android:layout_width="match_parent"
                android:layout_height="@dimen/tall_toolbar_height">

              <com.google.android.material.appbar.CollapsingToolbarLayout
                    android:id="+@id/collapsing_toolbar"
                  android:layout_width="match_parent"
                  android:layout_height="match_parent"
                  app:contentScrim="?attr/colorPrimary"
                  app:expandedTitleGravity="top"
                  app:layout_scrollFlags="scroll|exitUntilCollapsed|snap">

                <ImageView
                android:id="+@id/backdrop"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginTop="@dimen/shrine_toolbar_image_offset_top"
                app:layout_collapseMode="parallax"
                app:layout_collapseParallaxMultiplier="0.5"/>

                <android.support.v7.widget.Toolbar
                android:id="+@id/toolbar"
                    android:layout_width="match_parent"
                    android:layout_height="?attr/actionBarSize"
                    app:layout_collapseMode="pin"/>
              </com.google.android.material.appbar.CollapsingToolbarLayout>
            </com.google.android.material.appbar.AppBarLayout>
          </android.support.design.widget.CoordinatorLayout>

CollapsingToolbar.java
  
            ImageView imgHeader = findViewById(R.id.backdrop);
                  final CollapsingToolbarLayout collapsingToolbar = findViewById(R.id.collapsing_toolbar);
                  collapsingToolbar.setTitle(" ");
                  AppBarLayout appBarLayout = findViewById(R.id.appbar);
                  appBarLayout.setExpanded(true);

        // hiding & showing the txtPostTitle when toolbar expanded & collapsed
        appBarLayout.addOnOffsetChangedListener(new AppBarLayout.OnOffsetChangedListener() {
            boolean isShow = false;
            int scrollRange = -1;

            @Override
            public void onOffsetChanged(AppBarLayout appBarLayout, int verticalOffset) {
                if (scrollRange == -1) {
                    scrollRange = appBarLayout.getTotalScrollRange();
                }if (scrollRange + verticalOffset == 0) {
                    collapsingToolbar.setTitle(title);
                    isShow = true;
                } else if (isShow) {
                    collapsingToolbar.setTitle(" ");
                    isShow = false;
                }
            }
        });
            // loading toolbar header image
            Glide.with(getApplicationContext()).load(imageUrl)
                    .thumbnail(0.5f).transition(withCrossFade())
                    .apply(new RequestOptions()//.override(100, 100)
                            .error(R.drawable.ofline_page).centerCrop()
                    )
                    .into(imgHeader);
