
主要的程式在index.js

在 app.post('/webhook/', function (req, res) { 之中

首先先進行翻譯

            text = event.message.text
            input = text
            translate({
                text: input,
                source: 'en',
                target: 'fr'
            }, function (result) {
                console.log(result);
                final = String(result);
            }
 
 在自訂函數startprocess中運用setTimeout讓程式等待 3秒，再將回復信息(翻譯成法文後的句子)送出
 之後再用setTimeout讓程式在4秒後以clearTimeout清除startprocess裡的setTimeout
 
                        startprocess()
                        setTimeout(function () {
                          clearTimeout(start);}, 4000)
                        function startprocess() {
                           start = setTimeout(function () {
                                sendTranslation(sender, text.substring(0, 200));
                          }, 3000);
                        }
