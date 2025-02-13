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
        /* 每日养生金句样式 */
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
        /* 调整鼓励语模块样式 */
        #encouragementText {
            font-size: 1.5rem;
            font-weight: 600;
            color: #ff7f50; /* 温暖的橙色 */
            margin-top: 20px;
            text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.3);
            letter-spacing: 1px;
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
    </style>
</head>
<body>

<!-- 导航栏 -->
<nav class="navbar navbar-expand-lg bg-success text-white p-3">
    <div class="container">
        <a class="navbar-brand text-white" href=" ">静心养生茶</a >
    </div>
</nav>

<!-- 养生茶系列 -->
<div class="container py-5" id="products">
    <h2 class="text-center section-title mb-4">养生茶系列</h2>
    <div class="row">
        <div class="col-md-4 content-card" data-bs-toggle="modal" data-bs-target="#teaModal1">
            < img src="https://images.pexels.com/photos/1638280/pexels-photo-1638280.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" alt="安神助眠茶">
            <h3>安神助眠茶</h3>
        </div>
        <div class="col-md-4 content-card" data-bs-toggle="modal" data-bs-target="#teaModal2">
            < img src="https://images.pexels.com/photos/9443525/pexels-photo-9443525.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" alt="舒缓解压茶">
            <h3>舒缓解压茶</h3>
        </div>
    </div>
</div>

<!-- 养生穴位引导 -->
<div class="container py-5" id="acupoints">
    <h2 class="text-center section-title mb-4">养生穴位引导</h2>
    <div class="row">
        <div class="col-md-4 content-card" onclick="playVideo('https://example.com/taichong-acupoint.mp4')">
            < img src="https://tse2.mm.bing.net/th/id/OIP.QQ7yAKMj5jjU03XP2KR8lAHaD4?w=291&h=180&c=7&r=0&o=5&dpr=1.3&pid=1.7" alt="太冲穴">
            <h3>太冲穴</h3>
        </div>
        <div class="col-md-4 content-card" onclick="playVideo('https://example.com/neiguan-acupoint.mp4')">
            < img src="https://tse1.mm.bing.net/th/id/OIP.3TmYFVFX5Fh8sNqh3m7L9wHaEW?w=299&h=180&c=7&r=0&o=5&dpr=1.3&pid=1.7" alt="内关穴">
            <h3>内关穴</h3>
        </div>
    </div>
</div>

<!-- 养生音乐疗愈模块 -->
<div class="container py-5" id="music-therapy">
    <h2 class="text-center section-title mb-4">养生音乐疗愈</h2>
    <div class="row">
        <!-- 音乐疗愈卡片 -->
        <div class="col-md-4 acupoint">
            < img src="https://images.pexels.com/photos/29999123/pexels-photo-29999123.jpeg?auto=compress&cs=tinysrgb&w=600&lazy=load" alt="养生音乐疗愈" class="img-fluid rounded" id="musicImage" style="cursor: pointer;">
            <h3>音乐疗愈</h3>
            <p>点击图像即可播放养生音乐，带来舒缓放松效果。</p >
        </div>
    </div>
</div>

<!-- 音频播放器（隐藏） -->
<audio id="audioPlayer" style="display:none;" controls>
    <source src="https://music-1341782462.cos.ap-guangzhou.myqcloud.com/Inspiration.mp3" type="audio/mp3">
    您的浏览器不支持 audio 标签。
</audio>

<!-- JavaScript 代码 -->
<script>
    document.getElementById('musicImage').addEventListener('click', function() {
        var audio = document.getElementById('audioPlayer');
        audio.style.display = 'block';  // 显示音频播放器
        audio.play();  // 播放音频
    });

    // 预设的鼓励语库
    const encouragementMessages = [
        "无论遇到什么困难，都要相信自己，你一定能够克服。",
        "今天的努力，为明天的成功打下基础，加油！",
        "每一次挑战都是成长的机会，你正在变得更加坚强。",
        "相信自己，未来的你会感谢现在努力的自己。",
        "不必急于一时，静下心来，你会发现前方的路依然明亮。",
        "即使风雨再大，你也能撑起属于自己的晴空。",
        "每天都是新的开始，给自己一次重新出发的机会。",
        "勇敢走下去，成功就在不远处等你。",
        "永远记得，阳光总在风雨后，你已经走得很远。",
        "坚持下去，你就是最棒的！"
    ];

    // 随机生成一条鼓励语并显示
    document.getElementById('speakButton').addEventListener('click', function() {
        const randomIndex = Math.floor(Math.random() * encouragementMessages.length);
        const message = encouragementMessages[randomIndex];
        
        // 渐变显示效果
        const encouragementTextElement = document.getElementById('encouragementText');
        encouragementTextElement.textContent = message;
        encouragementTextElement.style.opacity = '0';  // 初始透明度为0
        setTimeout(function() {
            encouragementTextElement.style.opacity = '1';  // 逐渐显示
        }, 100);
    });

    // 播放指定的音乐视频
    function playVideo(url) {
        const videoElement = document.createElement('video');
        videoElement.src = url;
        videoElement.controls = true;
        videoElement.autoplay = true;
        document.body.appendChild(videoElement);
    }
</script>

<!-- Bootstrap 5 JS -->
<script src="https://cdn.bootcdn.net/ajax/libs/bootstrap/5.3.0/js/bootstrap.bundle.min.js"></script>
</body>
</html>
