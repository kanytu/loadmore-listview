loadmore-listview
=========================

**Listeners:**

    RefreshListener {
        /**
         * @param pageNumber page number
         * @param sampleSize sample size defined on xml parameters
         * @param listView   the listview itself
         * @param adapter    the adapter that you need to repopulate
         */
        void refresh(int pageNumber, int sampleSize, LoadingListView listView, BaseAdapter adapter);
    }

**Parameters:**

     sampleSize - The sample size. Used to check if your adapter has loaded all data or not

**XML usage:**

        <com.poliveira.apps.loadinglistview.LoadingListView
            android:id="@+id/loadingListView"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            app:sampleSize="5"/>

**Code usage**

        loadListview.setLoadMoreView(LayoutInflater.from(this).inflate(R.layout.loading, null));
        loadListview.setRefreshListener(new RefreshListener() {
            @Override
            public void refresh(final int pageNumber, int sampleSize, final LoadingListView listView, final BaseAdapter adapter) {
                if (pageNumber > 10)
                    listView.setLoadingRoutineFinished(); //stops the listview from loading more data
                else
                    fetchMyData(adapter);
            }
        });


**Output:**

![ParallaxListView](https://github.com/kanytu/loadmore-listview/blob/master/screenshots/teste.gif)
