
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
 })
 在運用setTimeout 跟 clearTimeout 讓程式等待 4秒，之後便將回復信息(翻譯成法文後的句子)送出
 
            startprocess()
            setTimeout(function () {
                clearTimeout(start);
            }, 4000)
        }
        if (event.postback) {
            text = JSON.stringify(event.postback)
            sendTextMessage(sender, "Postback received: " + text.substring(0, 200), token)
            continue
        }
    }
    res.sendStatus(200)
