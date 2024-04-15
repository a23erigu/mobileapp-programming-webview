
# Rapport

Detta lades till i AndroidManifest.xml för att göra så appen kunde nå internet.
```
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Jag skapade en WebView i activity_main.xml och gav den TheWebView som id.
```
<WebView
        android:id="@+id/TheWebView"
        android:layout_width="409dp"
        android:layout_height="326dp"
        android:layout_marginTop="160dp"
        android:layout_marginEnd="2dp"
        android:layout_marginRight="2dp"
        android:layout_marginBottom="190dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/appBarLayout"
        app:layout_constraintVertical_bias="1.0" />
```

I MainActivity.java skapades en WebView, WebViewClient och WebSettings.
```
private WebView myWebView;
private WebViewClient myWebViewCliente;
private WebSettings webSettings; 
```

I onCreate säts myWebView till WebViewn som hade skapats, myWebViewCliente sates som WebViewClient på myWebView 
och JavaScript activeras på myWebView. 
```
myWebView = findViewById(R.id.TheWebView);
myWebViewCliente = new WebViewClient();
myWebView.setWebViewClient(myWebViewCliente);

webSettings = myWebView.getSettings();
webSettings.setJavaScriptEnabled(true);
```

Till showExternalWebPage lades det till vilken url som skule ladas när de aktiverades.
```
public void showExternalWebPage(){
        myWebView.loadUrl("https://www.google.com/");
}
```

Till showInternalWebPage så skapades en html som heter InternalWebPage.html som används som url
```
public void showInternalWebPage(){
        myWebView.loadUrl("file:///android_asset/InternalWebPage.html");
}
```

Tillsist så lades det till så att showExternalWebPage och showInternalWebPage kördes när korekt knap tryktes.
```
if (id == R.id.action_external_web) {
        Log.d("==>","Will display external web page");
        showExternalWebPage();
        return true;
}

if (id == R.id.action_internal_web) {
        Log.d("==>","Will display internal web page");
        showInternalWebPage();
        return true;
}
```
Bilderna av appen

![](ExternalWebPage.png)

![](InternalWebPage.png)