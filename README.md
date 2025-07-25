COMO TRANSFORMAR SITE EM APLICATIVO COM ANDROID STUDIO WEBVIEW
 
Olá, pessoal! Hoje vou te mostrar como transformar qualquer site em um aplicativo para Android usando o Android Studio e WebView. É rápido, fácil e você vai aprender em menos de 90 segundos!

Primeiro, abra o Android Studio e crie um novo projeto. Escolha 'Empty Activity' e clique em 'Next'. Nomeie seu projeto, selecione a linguagem (Java ou Kotlin), e defina o nível mínimo de API.

Agora, vá até o arquivo `activity_main.xml` e substitua o layout padrão por uma WebView. Use este código aqui.

```xml
<WebView
    android:id="@+id/webview"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```

---

Em seguida, abra o arquivo `MainActivity` e adicione essas linhas de código. Primeiro, declare a WebView e configure a URL do seu site.

```java
import android.os.Bundle;
import android.webkit.WebView;
import android.webkit.WebViewClient;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        WebView webView = findViewById(R.id.webview);
        webView.setWebViewClient(new WebViewClient());
        webView.getSettings().setJavaScriptEnabled(true);
        webView.loadUrl("https://seusite.com");
    }
}
```

*(Se for Kotlin, mostre a versão equivalente.)*

---

Por último, não se esqueça de adicionar a permissão de internet no arquivo `AndroidManifest.xml`. Basta adicionar esta linha dentro da tag `<manifest>`.

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

---

Pronto! Agora é só executar o app no emulador ou em um dispositivo físico. Viu como é simples? Você acabou de criar um aplicativo que exibe seu site usando WebView!

Gostou do tutorial? Deixe seu like, se inscreva no canal e compartilhe com seus amigos. Até a próxima!
