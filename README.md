
# Rapport

**Skriv din rapport här!**

Först så byttes namnet på appen i Strings.xml. Sedan så fick appen internet tillstånd genom att lägga:

 <uses-permission android:name="android.permission.INTERNET" />

I filen AndroidManifest.xml. Sedan så skapades webvyn genom att ta bort textvyn som låg där sedan innan
och sedan dra in en webvy från menyn, sedan så resizeda jag den genom att dra runt lite samt pilla
lite i xml filen. Den fick även ett id. Sedan så skapades webvy koden. Det skapades en privat variabel
"my_webview" av typen WebView:

private WebView my_webview;

Sedan så hittades ID:et genom att lägga denna funktionen

my_webview = findViewById(R.id.my_webview);

Efter det skapades en WebViewClient och initierades genom att lägga dessa rader kod:

WebViewClient clientWebView = new WebViewClient();
        my_webview.setWebViewClient(clientWebView);

Sedan så gavs appen tillstånd att köra Javascript, detta gjordes genom att lägga dessa rader kod.

WebSettings webSettings = my_webview.getSettings();
        webSettings.setJavaScriptEnabled(true);

Den första hämtar inställningarna och den andra ändrar i inställningarna så det blir tillåtet att
köra Javascript.

Sedan så lades hemsidorna till genom att lägga till länken respektive sökvägen till html filen i
respektive funktion:

    public void showExternalWebPage(){

        my_webview.loadUrl("https://www.youtube.com/watch?v=L_jWHffIx5E");

    }

    public void showInternalWebPage(){

        my_webview.loadUrl("file:///android_asset/img/hello.html");

    }
    Det lades även till så att dessa metoder körs varje gång någon av knapparna i menyn trycks
    på, detta gjordes genom att lägga till metodernas namn i OnOptionsSelected på respektive plats:

     public boolean onOptionsItemSelected(MenuItem item) {
            // Handle action bar item clicks here. The action bar will
            // automatically handle clicks on the Home/Up button, so long
            // as you specify a parent activity in AndroidManifest.xml.
            int id = item.getItemId();

            //noinspection SimplifiableIfStatement
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

![intern websida](Screenshot1.png)
![extern websida](Screenshot2.png)
