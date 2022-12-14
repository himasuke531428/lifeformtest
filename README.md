<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>筋トレ管理</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" rossorigin="anonymous">
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/jqueryui/1.12.1/themes/base/jquery-ui.min.css">
</head>
<body>

    <form class="w-75 mx-auto">
        <p class="mt-3">名前</p>
        <div>
            <input class="form-control w-100 mt-1" name="name" placeholder="" required>
        </div>
        <p class="mt-3">腕立て</p>
        <div>
            <input class="form-control w-100 mt-1" name="udetate" required>
        </div>
        <p class="mt-3">腹筋</p>
        <div>
            <input class="form-control w-100 mt-1" name="fukkin" required>
        </div>
        <p class="mt-3">背筋</p>
        <div>
            <input class="form-control w-100 mt-1" name="haikin" required>
        </div>
        <p class="mt-3">スクワット</p>
        <div>
            <input class="form-control w-100 mt-1" name="sukuwat" required>
        </div>
        <input type="submit" class="mt-4 btn btn-primary" value="送信">
    </form>

    <script src="https://code.jquery.com/jquery-3.4.1.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jqueryui/1.12.1/jquery-ui.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.min.js" crossorigin="anonymous"></script>
    <script charset="utf-8" src="https://static.line-scdn.net/liff/edge/2.1/sdk.js"></script>
    <script>

        $(document).ready(function () {
            const liffId = "1657735528-KAO4aV6J";
            initializeLiff(liffId);
        })

        function initializeLiff(liffId) {
            liff.init({
                liffId: liffId
            }).then(() => {
                initializeApp();
            }).catch((err) => {
                console.log('LIFF Initialization failed ', err);
            });
        }

        function sendText(text) {
            liff.sendMessages([{
                'type': 'text',
                'text': text
            }]).then(function () {
                liff.closeWindow();
            }).catch(function (error) {
                window.alert('Failed to send message ' + error);
            });
        }

        const params = (new URL(document.location)).searchParams;
        const key = params.get('key');

        $(function () {
            $('form').submit(function () {
                const name    = $('input[name="name"]').val();
                const udetate = $('input[name="udetate"]').val();
                const fukkin  = $('input[name="fukkin"]').val();
                const haikin  = $('input[name="haikin"]').val();
                const sukuwat = $('input[name="sukuwat"]').val();
                const msg = `${name}\n${udetate}\n${fukkin}\n${haikin}\n${sukuwat}`;
                sendText(msg);
                return false;
            });
        });

    </script>

</body>
</html>
