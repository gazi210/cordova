<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <title>UClient</title>
    <!-- Sets initial viewport load and disables zooming  -->
    <meta name="viewport" content="initial-scale=1, maximum-scale=1">

    <!-- Makes your prototype chrome-less once bookmarked to your phone's home screen -->
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black">
    <link rel="stylesheet" href="css/mui.min.css" />
    <link rel="stylesheet" href="css/ratchet.css" />
    <style>
                .mui-table-view:after {
                    height: 0px;
                }
                /*.swipe {
            overflow: hidden;
            visibility: hidden;
            position: relative;
        }
        .swipe-wrap {
            overflow: hidden;
            position: relative;
        }
        .swipe-wrap > figure {
            float: left;
            width: 100%;
            position: relative;
        }
        #slider {
            max-width: 650px; 设置最大的宽度
            margin: 0px auto;  居中对齐
            height:40%;
        }
        .swipeimg{
                    max-width:100%;
                    height:auto;
                }
        figure {
            margin: 0; 对齐，四周宽度都为0，在轮播的时候，以整张图片进行移动
        }

        .table-view > li{
            float:left;
            width:150px;
            height:110px;
            position:relative;
        }

        .table-view > li > a > img{
            width:70px;
            height:70px;
        }
        .table-view > li > a > div{
            text-align:center;
        }
        .table-view-cell:after{
            height: 0px;
        }*/
    </style>
</head>
<body>
    <header class="bar bar-nav" style="background-image:url(images/blue22.png)">
        <h1 class="title" style="font-size:larger;color:white;">统一客户端</h1>
    </header>
    <nav class="bar bar-tab">
        <a class="tab-item active" href="index.html" data-ignore="push">
            <span class="icon icon-home"></span>
            <span class="tab-label">首页</span>
        </a>
        <a class="tab-item" onclick="showtip()">
            <span class="icon icon-person"></span>
            <span class="tab-label">Talk+</span>
        </a>
        <a class="tab-item" href="about.html" data-ignore="push">
            <span class="icon icon-gear"></span>
            <span class="tab-label">帮助</span>
        </a>
    </nav>

    <div class="content">
        <!--<div id="slider" class="swipe" style="visibility:visible;">
            <div class="swipe-wrap">
                <figure>
                    <div>
                        <img class="swipeimg" src="images/11.png" />
                    </div>
                </figure>
                <figure>
                    <div>
                        <img class="swipeimg" src="images/22.png" />
                    </div>
                </figure>
                <figure>
                    <div>
                        <img class="swipeimg" src="images/33.png" />
                    </div>
                </figure>
            </div>
        </div>

        <div>
            <ul class="table-view">
                <li class="table-view-cell media">
                    <a href="tmx_login.html">
                        <img src="images/gnome_session_properties.png">
                        <div class="media-body">工程实施</div>
                    </a>
                </li>
                <li class="table-view-cell media">
                    <a href="#">
                        <img src="images/preferences_contact_list.png">
                        <div class="media-body">运维响应</div>
                    </a>
                </li>
                <li class="table-view-cell media">
                    <a onclick="showtip()">
                        <img src="images/list_add.png">
                        <div class="media-body">订阅</div>
                    </a>
                </li>

            </ul>
        </div>-->
        <div id="slider" class="mui-slider">
            <div class="mui-slider-group mui-slider-loop">
                <div class="mui-slider-item mui-slider-item-duplicate">
                    <a href="#"><img src="images/33.png"></a>
                </div>
                <div class="mui-slider-item">
                    <a href="#"><img src="images/11.png"></a>
                </div>
                <div class="mui-slider-item">
                    <a href="#"><img src="images/22.png"></a>
                </div>
                <div class="mui-slider-item">
                    <a href="#"><img src="images/33.png"></a>
                </div>
                <div class="mui-slider-item mui-slider-item-duplicate">
                    <a href="#"><img src="images/11.png"></a>
                </div>
            </div>
            <div class="mui-slider-indicator">
                <div class="mui-indicator mui-active"></div>
                <div class="mui-indicator"></div>
                <div class="mui-indicator"></div>
            </div>
        </div>

        <ul class="mui-table-view mui-grid-view">
            <li class="mui-table-view-cell mui-media mui-col-xs-3">
                <a href="tm/tmx_login.html">
                    <img class="mui-media-object" src="images/gcss.png">
                    <div class="mui-media-body">工程实施1</div>
                </a>
            </li>
            <li class="mui-table-view-cell mui-media mui-col-xs-3">
                <a href="tm/tmdc_login.html">
                    <img class="mui-media-object" src="images/gcssdc.png">
                    <div class="mui-media-body">工程DC</div>
                </a>
            </li>
            <li class="mui-table-view-cell mui-media mui-col-xs-3">
                <a href="mct_index.html">
                    <img class="mui-media-object" src="images/ywyj.png">
                    <div class="mui-media-body">运维响应</div>
                </a>
            </li>

            <li class="mui-table-view-cell mui-media mui-col-xs-3">
                <a onclick="showtip()">
                    <img class="mui-media-object" src="images/list_add.png">
                    <div class="mui-media-body">订阅</div>
                </a>
            </li>
        </ul>
    </div>
    <script src="cordova.js"></script>
    <script type='text/javascript' src='lib/jquery-1.11.1.min.js'></script>
    <script src="lib/mui.min.js"></script>
    <script src="lib/toast.js"></script>
    <script>
    var first = null;
    
    document.addEventListener("backbutton", onBackKeyDown, false);
    function onBackKeyDown() {
    if (!first) {
    first = new Date().getTime();
    showtoast('再按一次退出应用');
    setTimeout(function () {
    first = null;
    }, 1000);
    } else {
    if (new Date().getTime() - first < 1000) {
    navigator.app.exitApp();
    }
    }
    }
    </script>
</body>
</html>
