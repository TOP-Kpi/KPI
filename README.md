<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🎉 生日快乐！🎉</title>
    <style>
        /* 内嵌 Plyr CSS */
        .plyr {
            --plyr-color-main: #ff69b4;
            --plyr-audio-controls-background: rgba(255, 255, 255, 0.8);
            --plyr-audio-control-color: #d81b60;
            --plyr-control-radius: 8px;
            --plyr-font-family: 'Microsoft JhengHei', 'Arial', sans-serif;
        }
        .plyr__control--overlaid {
            background: rgba(255, 105, 180, 0.8);
            border: 2px solid white;
        }
        .plyr--audio .plyr__controls {
            border-radius: 8px;
            padding: 10px;
        }
        
        body {
            font-family: 'Microsoft JhengHei', 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            background: linear-gradient(to bottom right, #ffe0f0, #cce5ff);
            color: #d81b60;
            text-align: center;
            flex-direction: column;
            overflow-x: hidden;
            position: relative;
            -webkit-touch-callout: none;
            -webkit-text-size-adjust: 100%;
            -webkit-font-smoothing: antialiased;
            -webkit-overflow-scrolling: touch;
        }

        .birthday-card {
            background-color: #ffffff;
            padding: 40px 60px;
            border-radius: 15px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
            animation: bounceIn 1s ease-out;
            max-width: 90%;
            width: 500px;
            box-sizing: border-box;
            position: relative;
            z-index: 10;
        }

        h1 {
            font-size: 2.8em;
            margin-bottom: 20px;
            color: #e91e63;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }

        #countdown {
            font-size: 1.5em;
            font-weight: bold;
            color: #880e4f;
            margin-top: 20px;
            margin-bottom: 20px;
        }

        button {
            margin-top: 20px;
            padding: 10px 25px;
            background-color: #ff69b4;
            color: white;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #ff85c1;
        }

        .confetti {
            position: fixed;
            width: 10px;
            height: 10px;
            background-color: #ff6b6b;
            top: -10px;
            animation: fall linear infinite;
            opacity: 0.8;
            border-radius: 20%;
            z-index: 1;
            will-change: transform, opacity;
        }

        @keyframes fall {
            0% {
                transform: translateY(0) rotateZ(0deg);
                opacity: 0.8;
            }
            100% {
                transform: translateY(100vh) rotateZ(720deg);
                opacity: 0;
            }
        }

        @keyframes bounceIn {
            0% { opacity: 0; transform: translateY(-100px); }
            60% { opacity: 1; transform: translateY(20px); }
            100% { transform: translateY(0); }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .message-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.6);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            backdrop-filter: blur(5px);
            animation: fadeIn 0.3s ease-out;
        }

        .message-box {
            background: linear-gradient(135deg, #f06292, #ef5350);
            color: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 5px 25px rgba(0,0,0,0.4);
            max-width: 80%;
            text-align: center;
            transform: scale(0.9);
            animation: popIn 0.3s cubic-bezier(0.68, -0.55, 0.27, 1.55) forwards;
        }
        .message-box p {
            font-size: 1.8em;
            margin-bottom: 25px;
            font-weight: bold;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.2);
        }
        .message-box button {
            background-color: #ffb74d;
            color: #880e4f;
        }
        .message-box button:hover {
            background-color: #ff9800;
        }

        @keyframes popIn {
            0% { transform: scale(0.7); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        #audio-container {
            margin: 20px auto;
            max-width: 400px;
            width: 100%;
        }

        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid rgba(255,255,255,.3);
            border-radius: 50%;
            border-top-color: #e91e63;
            animation: spin 1s ease-in-out infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        .ios-audio-hint {
            display: none;
            background: #fff8e1;
            padding: 10px;
            border-radius: 8px;
            margin: 10px 0;
            color: #ff6d00;
            font-size: 14px;
        }

        /* 响应式设计 */
        @media (max-width: 768px) {
            .birthday-card { padding: 30px 40px; }
            h1 { font-size: 2.5em; }
            #countdown { font-size: 1.2em; }
            .message-box p { font-size: 1.5em; }
        }
        @media (max-width: 480px) {
            .birthday-card { padding: 20px 25px; }
            h1 { font-size: 2em; }
            #countdown { font-size: 1em; }
            .message-box p { font-size: 1.2em; }
        }
    </style>
</head>
<body>
    <div class="birthday-card">
        <h1>🎉 生日快乐！🎉</h1>
        <img src="https://via.placeholder.com/200x200?text=加载中..." alt="生日照片" 
             style="width: 200px; height: 200px; border-radius: 50%; margin: 30px;"
             id="birthday-photo">
        
        <div id="countdown"></div>
        
        <div id="audio-container">
            <div class="ios-audio-hint" id="ios-audio-hint">
                ⚠️ iOS用户提示：请先点击屏幕任意处，然后点击播放按钮
            </div>
            <audio id="audio-player" controls playsinline>
                <!-- 音频将通过JavaScript内嵌 -->
            </audio>
            <button id="play-music-btn" style="display:none;">点击播放音乐</button>
        </div>
        
        <button onclick="toggleMessage()">显示祝福</button>
        <button onclick="customizePage()" style="margin-top:10px;">个性化设置</button>
    </div>

    <!-- 内嵌 Plyr JS -->
    <script>
        // 内嵌 Plyr 播放器库
        !function(e){"function"==typeof define&&define.amd?define(e):"object"==typeof exports?module.exports=e():e()}(function(){return function(e){var t={};function n(r){if(t[r])return t[r].exports;var o=t[r]={i:r,l:!1,exports:{}};return e[r].call(o.exports,o,o.exports,n),o.l=!0,o.exports}return n.m=e,n.c=t,n.d=function(e,t,r){n.o(e,t)||Object.defineProperty(e,t,{configurable:!1,enumerable:!0,get:r})},n.r=function(e){Object.defineProperty(e,"__esModule",{value:!0})},n.n=function(e){var t=e&&e.__esModule?function(){return e.default}:function(){return e};return n.d(t,"a",t),t},n.o=function(e,t){return Object.prototype.hasOwnProperty.call(e,t)},n.p="",n(n.s=4)}([function(e,t,n){"use strict";e.exports=function(e,t){return e===t||e!=e&&t!=t}},,,function(e,t,n){"use strict";e.exports=function(e,t){if(null==e)return{};var n,r,o={},i=Object.keys(e);for(r=0;r<i.length;r++)n=i[r],t.indexOf(n)>=0||(o[n]=e[n]);return o}},function(e,t,n){"use strict";var r=n(0),o=n(1),i=n(3);e.exports=function(e,t){if(!e)throw new Error("When calling withStyles in component, component can't be undefined");var n=t&&t.index?t.index:0;return function(t){var a=Object(o.default)(e,t);return Object(i.default)(a