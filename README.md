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
