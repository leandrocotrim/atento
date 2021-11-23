# atento

```cs
class Program
    {
        [STAThread]
        static void Main(string[] args)
        {
            const string uri = "http://beatrix-omni-vip.redecorp.br/cm-repository-client_l9_common/businessflows/repository/flows/NPC/web/ConfigureMultiProductsWidget.html";
            var webView = new WebViewJava.Inject.WebViewJava(uri);

            if (!webView.IsValid) return; // 😥😥😥😥😥😥😥😥😥


            // webView.Eval("alert('Fala Juci blz?')");

            var validateProducts = webView.GetElementsByAttribute("validationvalue", "validateProduct");
            var validateProduct = validateProducts.FirstOrDefault(element => element.innerText == "Validar");
            validateProduct.style.backgroundColor = "red";
            validateProduct.click();

            var stepId350422 = webView.GetElementsByAttribute("step-id", "350422").FirstOrDefault();
            stepId350422.click();

            var link = webView.GetElementsByTagName("a")
                .Where(a => a.innerHTML == "Adicionar" && !a.outerHTML.Contains("class=\"ux-npc__action--disabled\""))
                .ToList();

            link[0].style.color = "red";
            link[0].click();
            //link.outerHTML

            var error = GetError(webView);
            //tratar erro....


            var innerHtml = webView.InnerHTML;
        }

        public static string GetError(Inject.WebView webView)
        {
            var generalError = webView.GetElementById("generalError");
            if (generalError != null) return generalError.innerText;

            return null;
        }
    }
```
