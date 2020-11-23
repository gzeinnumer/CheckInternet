# CheckInternet

- Manifest
```xml
<manifest >

    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />

    ...

</manifest>
```

- Android 9 or Oldest

Not Realtime
```java
ConnectivityManager cm = (ConnectivityManager) getApplicationContext().getSystemService(Context.CONNECTIVITY_SERVICE);
boolean isConnect = cm.getActiveNetworkInfo() != null && cm.getActiveNetworkInfo().isConnected();

Log.d(TAG, "startNetworkCalilback: "+isConnect);
```

- Android 10

Realtime every connection connect or not
```java
ConnectivityManager cm = (ConnectivityManager) getApplicationContext().getSystemService(Context.CONNECTIVITY_SERVICE);
NetworkRequest.Builder builder = new NetworkRequest.Builder();

cm.registerNetworkCallback(builder.build(), new ConnectivityManager.NetworkCallback(){
    @Override
    public void onAvailable(@NonNull Network network) {
        super.onAvailable(network);
        Log.d(TAG, "onAvailable: true");
    }

    @Override
    public void onLost(@NonNull Network network) {
        super.onLost(network);
        Log.d(TAG, "onAvailable: false");
    }
});
```

---

```
Copyright 2020 M. Fadli Zein
```

