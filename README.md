<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>情绪养生茶包</title>
    <link href="https://cdn.bootcdn.net/ajax/libs/twitter-bootstrap/5.3.0/css/bootstrap.min.css" rel="stylesheet">
    <style>
        body {
            background: #f0f5e9;
            font-family: 'Microsoft YaHei', sans-serif;
        }
        .content-card {
            transition: transform 0.3s;
            cursor: pointer;
            background: #fff;
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            margin: 10px 0;
            text-align: center;
        }
        .content-card:hover {
            transform: translateY(-5px);
        }
        .content-card img {
            width: 100%;
            height: 150px;
            border-radius: 10px;
            object-fit: cover;
        }
        .section-title {
            background-color: #a8d08d;
            padding: 15px;
            border-radius: 5px;
        }
        #daily-quote {
            background: rgba(255, 255, 255, 0.8);
            padding: 20px;
            border-radius: 10px;
            text-align: center;
            font-size: 22px;
            font-weight: bold;
            border: 2px solid #d4af37;
            font-family: 'KaiTi', cursive;
            box-shadow: 0 0 10px rgba(212, 175, 55, 0.5);
            transition: opacity 1s ease-in-out;
        }
        #encouragementText {
            font-size: 1.5rem;
            font-weight: 600;
            color: #ff7f50;
            margin-top: 20px;
            text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.3);
            letter-spacing: 1px;
            opacity: 0; /* 初始透明度为0 */
            transition: opacity 1s ease-in-out;
        }
        #speakButton {
            margin-top: 30px;
            padding: 15px 30px;
            font-size: 1.2rem;
            font-weight: bold;
            background-color: #007bff;
            border: none;
            border-radius: 25px;
            transition: background-color 0.3s ease, transform 0.2s ease;
        }
        #speakButton:hover {
            background-color: #0056b3;
            transform: scale(1.05);
        }
        #speakButton:active {
            transform: scale(0.98);
        }
        /* 音频播放器样式 */
        #audioPlayerContainer {
            margin-top: 20px;
            text-align: center;
        }
        #audioPlayer {
            width: 100%;
            max-width: 500px;
        }
    </style>
</head>
<body>

<!-- 导航栏 -->
<nav class="navbar navbar-expand-lg bg-success text-white p-3">
    <div class="container">
        <a class="navbar-brand text-white" href=" ">静心养生茶</a >
    </div>
</nav>

<!-- 情绪价值互动模块（放置到页面顶部） -->
<div class="container py-5" id="emotional-value">
    <div class="row">
        <div class="col-md-12 text-center">
            <button id="speakButton">你说吧</button>
            <div id="encouragementText">我有🌹想对你说：你已经做得很好了，继续加油！</div>
        </div>
    </div>
</div>

<!-- 养生茶系列 -->
<div class="container py-5" id="products">
    <h2 class="text-center section-title mb-4">养生茶系列</h2>
    <div class="row">
        <div class="col-md-4 content-card" data-bs-toggle="modal" data-bs-target="#teaModal1">
            <img src="https://images.pexels.com/photos/1638280/pexels-photo-1638280.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" alt="安神助眠茶">
            <h3>安神助眠茶</h3>
        </div>
        <div class="col-md-4 content-card" data-bs-toggle="modal" data-bs-target="#teaModal2">
            <img src="https://images.pexels.com/photos/9443525/pexels-photo-9443525.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" alt="舒缓解压茶">
            <h3>舒缓解压茶</h3>
        </div>
    </div>
</div>

<!-- 养生穴位引导 -->
<div class="container py-5" id="acupoints">
    <h2 class="text-center section-title mb-4">养生穴位引导</h2>
    <div class="row">
        <div class="col-md-4 content-card" data-bs-toggle="modal" data-bs-target="#acupointModal1">
            <img src="https://tse2.mm.bing.net/th/id/OIP.QQ7yAKMj5jjU03XP2KR8lAHaD4?w=291&h=180&c=7&r=0&o=5&dpr=1.3&pid=1.7" alt="太冲穴">
            <h3>太冲穴</h3>
        </div>
        <div class="col-md-4 content-card" data-bs-toggle="modal" data-bs-target="#acupointModal2">
            <img src="https://tse1.mm.bing.net/th/id/OIP.3TmYFVFX5Fh8sNqh3m7L9wHaEW?w=299&h=180&c=7&r=0&o=5&dpr=1.3&pid=1.7" alt="内关穴">
            <h3>内关穴</h3>
        </div>
    </div>
</div>

<!-- 养生音乐疗愈模块 -->
<div class="container py-5" id="music-therapy">
    <h2 class="text-center section-title mb-4">养生音乐疗愈</h2>
    <div class="row">
        <div class="col-md-4 acupoint">
            <img src="https://images.pexels.com/photos/29999123/pexels-photo-29999123.jpeg?auto=compress&cs=tinysrgb&w=600&lazy=load" alt="养生音乐疗愈" class="img-fluid rounded" id="musicImage" style="cursor: pointer;" onclick="playMusic('https://music-1341782462.cos.ap-guangzhou.myqcloud.com/Inspiration.mp3')">
            <h3>音乐疗愈</h3>
            <p>点击图像即可播放养生音乐，带来舒缓放松效果。</p >
        </div>
    </div>
</div>

<!-- 音频播放器 -->
<div class="container" id="audioPlayerContainer">
    <audio id="audioPlayer" controls>
        <source src="https://music-1341782462.cos.ap-guangzhou.myqcloud.com/Inspiration.mp3" type="audio/mp3">
        您的浏览器不支持 audio 标签。
    </audio>
</div>

<!-- 茶包的模态框1 -->
<div class="modal fade" id="teaModal1" tabindex="-1" aria-labelledby="teaModalLabel" aria-hidden="true">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="teaModalLabel">安神助眠茶</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body">
                <p>这款茶包含了安神助眠的天然成分，适合在晚上饮用，帮助缓解压力和焦虑。</p >
                <ul>
                    <li>红枣：补血养颜，安神</li>
                    <li>枸杞：滋补肝肾，助眠</li>
                    <li>茉莉花：舒缓身心，改善睡眠质量</li>
                </ul>
                <img src="https://images.pexels.com/photos/1638280/pexels-photo-1638280.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" class="img-fluid" alt="安神助眠茶">
            </div>
        </div>
    </div>
</div>

<!-- 茶包的模态框2 -->
<div class="modal fade" id="teaModal2" tabindex="-1" aria-labelledby="teaModalLabel" aria-hidden="true">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="teaModalLabel">舒缓解压茶</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body">
                <p>这款茶含有多种舒缓压力的成分，适合工作压力大的时候饮用，帮助缓解紧张情绪。</p >
                <ul>
                    <li>菊花：清热解毒，舒缓压力</li>
                    <li>薄荷：清凉解暑，放松身体</li>
                    <li>柠檬：提神醒脑，缓解疲劳</li>
                </ul>
                <img src="https://images.pexels.com/photos/9443525/pexels-photo-9443525.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" class="img-fluid" alt="舒缓解压茶">
            </div>
        </div>
    </div>
</div>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>养生产品页面</title>
    <link rel="stylesheet" href="styles.css"> <!-- 样式文件 -->
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script> <!-- jQuery -->
    <!-- 养生产品相关内容 -->
    <div class="product-details">
        <h1>养生茶包</h1>
        <p>享受温暖舒缓的茶时光，舒缓身心，调理健康。</p >
        <button data-toggle="modal" data-target="#modal1">查看穴位引导</button>
        <button data-toggle="modal" data-target="#modal2">查看穴位引导</button>
    </div>
    <!-- 第一个养生穴位引导模态框 -->
    <div id="modal1" class="modal">
        <div class="modal-content">
            <span class="close" data-dismiss="modal">&times;</span>
            <h2>养生穴位引导 1</h2>
            <p>点击以下链接查看详细的养生穴位引导视频或动图。</p >
            点击查看视频或动图
        </div>
    </div>
    <!-- 第二个养生穴位引导模态框 -->
    <div id="modal2" class="modal">
        <div class="modal-content">
            <span class="close" data-dismiss="modal">&times;</span>
            <h2>养生穴位引导 2</h2>
            <p>点击以下链接查看详细的养生穴位引导视频或动图。</p >
            点击查看视频或动图
        </div>
    </div>
    <!-- 模态框的CSS样式 -->
    <style>
        .modal {
            display: none;
            position: fixed;
            z-index: 1;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            overflow: auto;
            background-color: rgb(0,0,0);
            background-color: rgba(0,0,0,0.4);
        }
        .modal-content {
            background-color: #fefefe;
            margin: 15% auto;
            padding: 20px;
            border: 1px solid #888;
            width: 80%;
        }
        .close {
            color: #aaa;
            float: right;
            font-size: 28px;
            font-weight: bold;
        }
        .close:hover,
        .close:focus {
            color: black;
            text-decoration: none;
            cursor: pointer;
        }
    </style>
    <!-- JavaScript部分 -->
    <script>
        // 打开模态框的功能
        $(document).ready(function(){
            $('[data-toggle="modal"]').click(function(){
                var target = $(this).data('target');
                $(target).fadeIn();
            });
            // 关闭模态框的功能
            $('.close').click(function(){
                $(this).closest('.modal').fadeOut();
            });
            // 点击外部区域关闭模态框
            $(window).click(function(event) {
                if ($(event.target).hasClass('modal')) {
                    $(event.target).fadeOut();
                }
            });
        });
<!-- Bootstrap 5 JS -->
<script src="https://cdn.bootcdn.net/ajax/libs/bootstrap/5.3.0/js/bootstrap.bundle.min.js"></script>

<script>
    // 更新播放音乐的函数
    function playMusic(url) {
        const audioPlayer = document.getElementById('audioPlayer');
        if (audioPlayer.paused) {
            audioPlayer.src = url;
            audioPlayer.play();
        } else {
            audioPlayer.pause();
        }
    }

    // 情绪鼓励语交互（我有话想对你说）
    const speakButton = document.getElementById('speakButton');
    const encouragementTextElement = document.getElementById('encouragementText');
    const encouragementMessages = [
        "我有🌹想对你说：你已经做得很好了，继续加油！",
        "我有🌹想对你说：你今天非常努力，相信自己，未来一定光明！",
        "我有🌹想对你说：你踏出的每一步都为你创造了更好的明天！"
    ];
    speakButton.addEventListener('click', function() {
        const randomMessage = encouragementMessages[Math.floor(Math.random() * encouragementMessages.length)];
        encouragementTextElement.textContent = randomMessage;
        encouragementTextElement.style.opacity = '0';  // 初始透明度为0
        setTimeout(function() {
            encouragementTextElement.style.opacity = '1';  // 逐渐显示
        }, 100);
    });
</script>

</body>
</html>
