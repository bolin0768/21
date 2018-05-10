
<!DOCTYPE html>

<html lang="en" xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0" />
    <title></title>
    <style>
        .preview-tip {position:absolute;left:0;top:-80px;height:80px;line-height:20px;color:#fff;width:100%;background:rgba(248,110,36,.8);z-index:999;padding:10px 15px;font-size:14px;box-sizing:border-box;-webkit-transition:all 500ms;-moz-transition:all 500ms;transition:all 500ms;}
        .preview-tip-remove {display:inline-block;vertical-align:-1px;cursor:pointer;width:10px;}
        .preview-tip-span {display:inline-block;vertical-align:middle;cursor:pointer;font-size:12px;}
        .preview-tip-oper {position:absolute;bottom:5px;right:25px;}
        .preview-thinsp {background-color:#fff;margin:0 8px;height:14px;}

        .preview-mask {position:absolute;left:0;top:0;width:100%;height:100%;background:#000;z-index:9999;display:none;}
        .preview-dialog {position:absolute;padding:10px 34px;background:#fff;border-radius:3px;height:180px;margin-top:-90px;left:50%;top:50%;box-sizing:border-box;box-shadow: 0px 0px 4px grey;}
        .preview-dialog *{box-sizing:border-box;font-family:Microsoft Yahei, Arial;}
        .preview-dialog-row {margin-left:-5px;margin-right:-5px;}
        .preview-dialog-label {font-size:14px;text-align:center;margin:5px 0;color:#555;}
        .preview-dialog-input {border:1px solid #555;border-radius:3px;width:100%;height:32px;padding:2px 4px;-webkit-appearance: none; color:#555;font-size:14px;}
        .preview-dialog-input:focus {outline-width: 0;}
        .preview-dialog-error {font-size:12px;text-align:left;margin-top:2px;color:#ff3a3a;}
        .preview-dialog-button {width:80px;height:32px;line-height:26px;border:none;color:#fff;cursor:pointer;}
        .preview-dialog .preview-sure {background:#f4901e;width:100px;}
        .preview-dialog .preview-cancel {background:#bebebe;float:right;display:none;}
        .error {border:1px solid #ff3a3a;}
        .center {text-align:center;}
        .mt40 {margin-top:40px;}
        .mt30 {margin-top:30px;}
        .mt20 {margin-top:20px;}
        .mt15 {margin-top:15px;}
        .mt10 {margin-top:10px;}
    </style>
    <script>
    function setCookie(c_name,value,expiredays){var exdate=new Date();var domain_parts=window.location.host.split('.');var len=domain_parts.length;var domain='';if(len>=2){domain='.'+domain_parts[len-2]+'.'+domain_parts[len-1];}else{domain='.mugeda.com';}exdate.setDate(exdate.getDate()+expiredays);document.cookie=c_name+"="+escape(value)+((expiredays==null)?"":";expires="+exdate.toGMTString())+"; domain="+domain+";path=/";}
    if (/vt=(\w+)\&?/.test(location.search)) {
        var versionTag = RegExp.$1;
        setCookie('__mugeda_vid',versionTag,60*60*24*3600);
    } else {
        setCookie('__mugeda_vid','',-3600);
    }
    </script>
</head>                   
<body style="margin:0;padding:0;overflow:hidden;">
    <div class="preview-tip" id="previewTip">
        <div id="previewTipContent">Mugeda IDE Tip Message Mugeda IDE Tip Message Mugeda IDE Tip Message</div>
        <div id="previewTipOper" class="preview-tip-oper">
            <span class="preview-tip-span" id="tip-nomore">不再提醒</span>
            <span class="preview-tip-span preview-thinsp">&thinsp;</span>
            <span class="preview-tip-span" id="tip-close">
                关闭
                <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAOCAYAAAAfSC3RAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAA3ppVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNS1jMDIxIDc5LjE1NTc3MiwgMjAxNC8wMS8xMy0xOTo0NDowMCAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wTU09Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9tbS8iIHhtbG5zOnN0UmVmPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvc1R5cGUvUmVzb3VyY2VSZWYjIiB4bWxuczp4bXA9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC8iIHhtcE1NOk9yaWdpbmFsRG9jdW1lbnRJRD0iOTZFRUY3MUEwNkZERERDMTA0RkJCM0IxRTlGNzU3NzYiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6Qjg4NTZFNjY1NkFCMTFFNThEQjI4NjQzMjU3OENGQzEiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6Qjg4NTZFNjU1NkFCMTFFNThEQjI4NjQzMjU3OENGQzEiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIDIwMTQgKE1hY2ludG9zaCkiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDphN2JkOTU0Ny00MTdjLTRmM2QtYjNlZC1mZmU4NjU4ZmYzYWIiIHN0UmVmOmRvY3VtZW50SUQ9ImFkb2JlOmRvY2lkOnBob3Rvc2hvcDpmMzVjYmIzMS05MTAxLTExNzgtODE2Ni04Zjk0N2Q2MTQyOWMiLz4gPC9yZGY6RGVzY3JpcHRpb24+IDwvcmRmOlJERj4gPC94OnhtcG1ldGE+IDw/eHBhY2tldCBlbmQ9InIiPz5vJwwTAAAAgklEQVR42ozSYQqAIAwF4Nmp6jh6q/pR1+lOBfYGKss2W/DClh/KWMg5r0R0Igf5nogsBJiQC4kI/YT33GxqwYMb4m/5Y4RfqIcWjqWW5F7tShKryIISq4gzGS3PxlpU9UbUk8yGjdCw23/IxB7U4zYAHvTBAa+tDPnuHPKEzI8AAwDS9/8JtETnyAAAAABJRU5ErkJggg==" class="preview-tip-remove" />
            </span>
        </div>
    </div>
    <div class="preview-mask" id="previewMask">
        <div class="preview-dialog" id="previewDialog">
             <div class="preview-dialog-row">
                 <p class="preview-dialog-label">你要查看的内容受到密码保护</p>
                 <p class="preview-dialog-label">请输入密码：</p>
             </div>
             <div class="preview-dialog-row mt10">
                 <input type="number" class="preview-dialog-input" id="previewDialogInput" />
                 <p class="preview-dialog-label preview-dialog-error" id="previewDialogError">&nbsp;</p>
             </div>
             <div class="preview-dialog-row mt15 center">
                 <button class="preview-dialog-button preview-sure" id="previewSure">确认</button>
                 <button class="preview-dialog-button preview-cancel" id="previewCancel">取消</button>
             </div>
        </div>
    </div>
    <script src="/mugeda_client_utils/js/forceInspectChk.js"></script>
    <script src="/mugeda_client_utils/js/mugeda_local_storage.js"></script>
    <script src="js/preview_tip.js"></script>
    <script src="/mugeda_client_utils/js/mugeda_loader_all.js"></script>
    <!--<script src="/mugeda_client_utils/js/mugeda_plugin_dependence.js"></script> -->
    <!--<script src="../mugeda_client_utils/js/mugeda_loader_circle.js"></script>-->
    <script src="//card.mugeda.com/scripts/config_prev.js"></script>
    <div id="frame" class="MugedaStage">
        <script>
            (function () {
                var loadScripts = function (data, callback) {
                    var loadCount = 0;
                    var loadScript = function (src, loadCall) {
                        var head = document.getElementsByTagName('head')[0];
                        var script = document.createElement('script');
                        script.type = 'text/javascript';
                        script.src = src;
                        loadCount++;
                        script.onload = function () {
                            if (loadCall) loadCall(0);
                            loadCount--;
                            if (loadCount == 0 && callback)
                                callback();
                        };
                        script.onerror = function (e) {
                            if (loadCall) loadCall(-1);
                            console.log('Error in loading ' + src);
                            loadCount--;
                            if (loadCount == 0 && callback)
                                callback();
                        };
                        head.appendChild(script);
                    };

                    if (data.sL) {
                        if (data.sL.jquery) {
                            loadScript("js/jquery-1.10.2.min.js");
                        }
                        if (data.sL.qrcode) {
                            if (!data.sL.jquery)
                                loadScript("js/jquery-1.10.2.min.js");

                            // This library needs to wait for jQuery being ready
                            loadCount++;
                            var loadAsync = function () {
                                if (typeof jQuery == "undefined") {
                                    setTimeout(loadAsync, 50);
                                }
                                else {
                                    loadCount--;
                                    loadScript("js/jquery.qrcode.min.js");
                                    loadScript("js/qrcode.min.js");
                                }
                            };
                            loadAsync();
                        }
                        if (data.sL.box2d) {
                            loadScript("js/Box2dWeb-2.1.a.3.min.js");
                        }
                        if (data.sL.cardCommon) {
                            var regex = /micromessenger\/(\d+).(\d+).?(\d?)\s?/;
                            var items = navigator.userAgent.toLowerCase().match(regex);
                            var wechatVersion = 0.0;
                            if(items && items.length > 3)
                                wechatVersion = items[1] +'.'+ items[2] + '' + items[3];
 
                            // [Lucas] 这段加载Wechat JS SDK的逻辑移到了card_common里面了。
                            // Card_common处理所有的微信逻辑，这两个必须同时加载，因此就交给card_common处理。
                            // 否则，发布到CDN后，没有preview_css.html了，这个文件就没人负责加载了。
                            // var isNewWeiXIn = wechatVersion > 6.015;
                            // if(isNewWeiXIn)
                            //     loadScript("http://res.wx.qq.com/open/js/jweixin-1.0.0.js");
                        }
                        if (data.sL.socketio) {
                            loadScript("js/socket.io.1.9.16.min.js");
                            loadScript("/mugeda_client_utils/js/mugeda_connection.js");
                        }
                    }
                    if (loadCount == 0 && callback)
                        callback();
                }

                function ajax(o) { var b = /POST/i.test(o.type), p = o.data || '', t = o.dataType, url = o.url || location.href, q = /\?/.test(url) ? '&' : '?', x = window.XMLHttpRequest ? new XMLHttpRequest() : (new ActiveXObject('Msxml2.XMLHTTP') || new ActiveXObject('Microsoft.XMLHTTP')), z = function (s) { if (x.readyState == 4) { if (x.status == 200) { s = x.responseText; if (t == 'json') s = json(s); if (b = o.success) b(s) } else if (x.status == 0 && x.response) { s = x.response; if (t == 'json') s = json(s); if (b = o.success) b(s) } else if (o.error) { o.error(x.status, x) } } }; x.onreadystatechange = z; if (typeof p == 'object') { var r = []; for (var k in p) r.push(encodeURIComponent(k) + '=' + encodeURIComponent(p[k])); p = r.join('&') } x.open(b ? 'POST' : 'GET', url + (b ? '' : ((p ? q : '') + p + (o.cache ? '' : (((!p && q == '?') ? '?' : '&') + '_=' + new Date().getTime())))), o.async === false ? false : true); if (b) x.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded'); x.send(p); return x; }

                function json(s) {
                    try {
                        return eval('(' + s + ')')
                    } catch (e) {
                        return null
                    }
                }

                function getQueryStringRegExp(name) {
                    var reg = new RegExp("(^|\\?|&)" + name + "=([^&]*)(\\s|&|$)", "i");
                    if (reg.test(location.href)) return unescape(RegExp.$2.replace(/\+/g, " ")); return "";
                };

                // 绑定微信加载完成事件，以预加载声音
                (function () {
                    var is_weixin = (function () {
                        var ua = navigator.userAgent.toLowerCase();
                        if (ua.match(/MicroMessenger/i) == "micromessenger") {
                            return true;
                        } else {
                            return false;
                        }
                    })();
                    var auStr = getQueryStringRegExp('audio');
                    if (auStr) {
                        auStr = decodeURI(auStr);
                        var auList = [];
                        try {
                            auList = JSON.parse(auStr)
                        }
                        catch (ex) {
                            console.error('cannot solve audio param.')
                        }
                        window.weixinAudioLoader = {};
                        for (var i = 0; i < auList.length; i++) {
                            var url = auList[i].u,
                                isAutoPlay = (auList[i].a != '0');
                            var dom = window.weixinAudioLoader[url] = new Audio(url);
                            //if (isAutoPlay) { dom.autoplay = true; }
                            dom._play = dom.play;
                            dom._pause = dom.pause;
                            dom.play = function () {
                                if (dom.weixinLoaded || !is_weixin) {
                                    dom._play.call(dom);
                                }
                                else {
                                    dom.weixinPlayCalled = true;
                                }
                            }
                            dom.pause = function () {
                                if (dom.weixinLoaded || !is_weixin) {
                                    //dom.currentTime = dom.duration;
                                    dom._pause.call(dom);
                                }
                                else {
                                    dom.weixinPlayCalled = false;
                                }
                            }

                        }
                    }
                    document.addEventListener('WeixinJSBridgeReady', function onBridgeReady() {
                        for (var url in window.weixinAudioLoader) {
                            var dom = window.weixinAudioLoader[url];
                            dom.load();
                            dom.addEventListener('canplay', function () {
                                if (dom.weixinPlayCalled) {
                                    dom._play.call(dom);
                                    delete dom.weixinPlayCalled;
                                }
                                else {
                                    // dom.currentTime = dom.duration;
                                }
                                dom.weixinLoaded = true;
                            })
                        }
                    });
                })();


                // 定义动画id
                var creationTag = "preview";
                // 定义资源文件的目录
                var resourceRelativeDir = "";
                // 定义mudega_css3_player.js文件的位置
                var css3playerDir = "/mugeda_client_utils/js/";
                // 唯一标志，以便在用户脚本中引用这个动画
                var id = "my";

                window._mrmcp = window._mrmcp || {};
                window._mrmcp.previewMode = true;
                top.contentid && (window._mrmcp.creative_id = top.contentid);
                
                // ********************
                // * 以下部分不要修改 *
                // ********************

                if (typeof (Mugeda) == "undefined") { Mugeda = {}; Mugeda.data = {} }
                Mugeda.previewMode = true;
                if (!Mugeda.Loader) {
                    Mugeda.Loader = function (creationTag, dom, autoStart, resourceDir, playerLoc, id) {
                        if (!creationTag) throw ("creation identify not defined");
                        this.id = creationTag;
                        this.name = id;
                        var scriptTag = document.getElementsByTagName('script');
                        scriptTag = scriptTag[scriptTag.length - 1];
                        this.dom = dom || scriptTag;
                        this.resDir = resourceDir || "";
                        this.playerLoc = playerLoc || "";
                        autoStart = (autoStart == undefined ? true : autoStart);

                        var loadJs = function (src, callback) {
                            if (isLoaded(src)) {
                                if (callback) callback();
                                return;
                            }
                            var objDynamic = document.createElement("script");
                            objDynamic.src = src;
                            document.getElementsByTagName("head")[0].appendChild(objDynamic);
                            // objDynamic.onload = objDynamic.onreadystatechange = function () {
                            objDynamic.onload = function () {
                                // if (this.readyState == undefined || this.readyState == "loading")
                                //     return;
                                /// else
                                if (callback) {
                                    callback();
                                    callback = function () { };
                                };
                            }
                        }

                        var isLoaded = function (src) {
                            var scripts = document.getElementsByTagName("script");
                            var isLoaded = false;
                            for (i = 0; i < scripts.length; i++) {
                                if (scripts[i].src && scripts[i].src.indexOf(src) != -1) {
                                    if (scripts[i].readyState == "loaded" || scripts[i].readyState == "complete") {
                                        isLoaded = true;
                                        break;
                                    }
                                }
                            }
                            return isLoaded;
                        }

                        var use3D = "auto";
                        var buildno = 0;
                        if (/use3(d|D)=(\w+)\&?/.test(location.search)) {
                            use3D = RegExp.$2;
                        }
                        if (/buildno=(.*)\&?/.test(location.search)) {
                            buildno = RegExp.$1;
                        }
                        
                        var that = this;

                        var loadPlugin = function(callback){
                            var anidata = Mugeda.data["id_" + creationTag] || {};
                            var metadata = anidata.metadata || {};
                            var publishMode = metadata.publishMode || "player";
                            if(publishMode == "smart" ){
                                /*
                                loadJs(that.playerLoc + 'mugeda_smart_renderer_inputbox.js' + "?buildno=" + buildno, function () {
                                    loadJs(that.playerLoc + 'mugeda_smart_renderer_chooseimage.js' + "?buildno=" + buildno, function () {
                                        callback();
                                    });
                                });*/
                                var loadStatusHash = {core: 2};
                                var plugs = (anidata.plugin || []);
                                //var plugList = Object.keys(MugedaPlugDependency)
                                /*
                                 var plugName =  instance.plugins[plugin].plug;
                                 if(plugName == 'core')
                                 continue;
                                 else
                                 command.push(SmartConverter.CopyFile(path.resolve(instance.manifest.utilPath, './mugeda_client_utils/js/mugeda_smart_renderer_' + plugName + '.js'), path.resolve(instance.manifest.manifestPath, './mugeda_smart_renderer_' + plugName + version + '.js')));
                                 */
                                var plugHash = {};
                                plugs.forEach(function(plug){
                                    plugHash[plug.plug] = JSON.parse(plug.deps).map(function(dep){ return plugs[dep * 1].plug; });
                                });
                                var loadNext = function() {
                                    var unloadedPlugs = Object.keys(plugHash).filter(function(plugName){
                                        return (loadStatusHash[plugName] || 0) < 2;
                                    });
                                    if(unloadedPlugs.length == 0){
                                        callback();
                                    }
                                    else {
                                        unloadedPlugs.forEach(function (plugName) {
                                            var plugLoadStatus = loadStatusHash[plugName] || 0;
                                            if (plugLoadStatus == 0) {
                                                var deps = plugHash[plugName];
                                                if (deps.some(function (depPlugName) {
                                                            return loadStatusHash[depPlugName] < 2;
                                                        })) {
                                                    return;
                                                }
                                                loadStatusHash[plugName] = 1;
                                                loadJs(that.playerLoc + 'mugeda_smart_renderer_' + plugName + ".js?buildno=" + buildno, function () {
                                                    loadStatusHash[plugName] = 2;
                                                    loadNext();
                                                });
                                            }
                                        });
                                    }
                                };
                                loadNext();
                            }
                            else{
                                callback();
                            }

                        };
                        
                        var loadPlayer = function(callback){
                            // 检查css3Player是否加载
                            if (!Mugeda.css3PlayerLoaded) {
                                // 异步载入js文件
                                var anidata = Mugeda.data["id_" + creationTag] || {};
                                var metadata = anidata.metadata || {};
                                var publishMode = metadata.publishMode || "player";
                                var player = publishMode == "smart" ? "mugeda_smart_renderer.js" : "mugeda_css3_player.js";
                            
                                var loadNum = 2;
                                var checkLoadNum = function(){
                                    loadNum--;
                                    if(loadNum == 0)
                                        callback && callback();
                                }
                                loadJs(that.playerLoc + "" + player + "?buildno=" + buildno, function () {
                                    var ua = navigator.userAgent.toLowerCase();
                                    var isAndroid = ua.indexOf("android") > -1;
                                    var androidVersion = parseFloat(ua.slice(ua.indexOf('android') + 8));

                                    if (use3D != "off" && (use3D == "on" || !isAndroid || androidVersion > 3.5))
                                        Mugeda.enable3DRendering(true);
                                    
                                    checkLoadNum();
                                });
                                loadJs(that.playerLoc + "mugeda_utils.js?buildno=" + buildno, function(){
                                    checkLoadNum();
                                });
                                //loadJs(that.playerLoc + "mraid.js");
                                Mugeda.css3PlayerLoaded = 1;
                            }
                        }
                        
                        
                        // 异步载入anidata文件,回调
                        //loadJs(this.id + ".js", function () {
                        //    if (autoStart) that.start();
                        //});

                        if (/id=(\w+)\&?/.test(location.search)) {
                            var contentid = RegExp.$1;
                            loadUrl = '/myani/load';

                            var isProtected = getQueryStringRegExp('protected');
                            if (isProtected == 1) {
                                MuPTip.showPasswordDialog();
                                MuPTip.bindEvent(contentid);
                                return;
                            }

                            ajax({
                                type: "GET",
                                url: loadUrl,
                                data: {
                                    contentid: contentid
                                },
                                dataType: "text",
                                success: function (s) {
                                    var metaData;
                                    if (metaData = json(s)) {
                                        s = json(metaData.data);
                                    } else {
                                        window.location.href = '/preview/error/0';
                                        return;
                                    }

                                    if (16 === metaData.status) {
                                        window.location.href = '/preview/error/1';
                                        return;
                                    } else if (19 === metaData.status){
                                        window.location.href = '/preview/error/2';
                                        return;
                                    } else if (4 === metaData.status) {
                                        window.location.href = '/preview/error/0';
                                        return;
                                    }

                                    var credits = metaData ? (metaData.credit_point || 0) : 0;
                                    var min_credit = 100;
                                    var reasons = [];
                                    var isRegression = navigator.userAgent.indexOf('MugedaRegressionTest') > 0;
                                    !isRegression && MugedaForceInspectChk.check({
                                        aniData: s,
                                        callback: function(risk, list, risk){
                                            risk.map(function(item){
                                                if(['js', 'xss', 'expression'].indexOf(item.type)>=0){
                                                    if(credits > min_credit){
                                                    }
                                                    else {
                                                        s=null;
                                                        reasons.push(item.type);
                                                    }                                                    
                                                }
                                            });        
                                        }
                                    });
                                    
                                    if (metaData && metaData.share_error === 1) {
                                        MuPTip.showPasswordDialog();
                                        MuPTip.bindEvent(contentid);
                                        return;
                                    } else if (!s) {
                                        window.location.href = reasons.length ? 'preview_ban.html?reasons='+reasons.join(',')+'&url='+encodeURIComponent(window.location.href) : "/preview/error/0";
                                        return;
                                    }

                                    // if (metaData.is_share) {
                                    //     var tip = '此链接仅供预览。如果想要发布使用，请在Mugeda后台使用“发布”功能。';
                                    //     if (metaData.server === 'INTERNATIONAL') {
                                    //         tip = 'This content is for preview only. Please publish the content at mugeda.com.';
                                    //     }
                                    //     if (window.location.hostname.indexOf('mugeda.com') === -1) {
                                    //         tip = tip.replace('Mugeda', '');
                                    //     }

                                    //     MuPTip.showTopMessage(tip, metaData.share_count || 1024);
                                    // }

                                    window._mrmcp.creative_id = metaData.crid;
                                    if (metaData.partner !== 'mugeda') {
                                        for (var key in metaData['_mrmcp']) {
                                            if (metaData['_mrmcp'].hasOwnProperty(key)) {
                                                _mrmcp[key] = metaData['_mrmcp'][key];
                                            }
                                        }
                                    }

                                    aniData = s;
                                    Mugeda.data = Mugeda.data || {};
                                    Mugeda.data.crid = metaData.crid || '';
                                    Mugeda.data["id_" + creationTag] = aniData;
                                    if(navigator.userAgent.toLowerCase().indexOf('micromessenger') > -1 && aniData.wxRedirectType && location.href.indexOf('token=') == -1){
                                        return location.href = "//weika.mugeda.com/server/card/token?type="+aniData.wxRedirectType+"&force_refresh=0&redirect=" + encodeURIComponent(location.href);
                                    }


                                    loadScripts(aniData, function () {
                                        loadPlayer(function(){
                                            loadPlugin(function(){
                                                if (autoStart) that.start();
                                            });
                                        });
                                    });
                                }
                            });
                        }
                        else if (parent.AniData) {
                            setTimeout(function () {
                                Mugeda.data["id_" + creationTag] = JSON.parse(parent.AniData);
                                loadScripts(Mugeda.data["id_" + creationTag], function () {
                                    loadPlayer(function(){
                                        loadPlugin(function(){
                                            if (autoStart) that.start();
                                        });
                                    });
                                });
                            }, 0);
                        }

                    }

                    Mugeda.Loader.prototype.start = function () {
                        var anidata = Mugeda.data["id_" + creationTag];
                        
                        document.body.style.backgroundColor = (anidata.cl || anidata.color || "rgb(255,255,255)");

                        // 开始动画
                        if (Mugeda.css3PlayerLoaded == 2) {
                            // 若播放器已经加载，直接加载动画
                            var stage = document.createElement("div");
                            this.dom.parentNode.insertBefore(stage, this.dom);
                            Mugeda.startAnimation("id_" + this.id, null, stage, this.resDir, this.name);
                        }
                        else {
                            // 若播放器没有加载，将其放在一个列表中，等播放器加载完成后加载动画
                            Mugeda.creationToBeLoad = Mugeda.creationToBeLoad || [];
                            Mugeda.creationToBeLoad.push(this);
                        }
                    }
                }

                var loader = new Mugeda.Loader(creationTag, null, null, resourceRelativeDir, css3playerDir, id);
            })();
        </script>
        <script>
            (function () {
                // 在舞台上插入未发布标示
                function findStage() {
                    var _stage = document.querySelector('[data-type="stage"]');
                    var _time;
                    if (_stage) {
                        var node = document.createElement('div');
                        node.style = 'position:absolute;opacity:.7;pointer-events:none;'
                        node.innerHTML = '<img width="90" src="./res/issue.svg">';
                        _stage.appendChild(node)
                        return;
                    } else {
                        _time = setTimeout(function () {
                            findStage();
                            clearTimeout(_time);
                        }, 100);
                    }
                }

                // 判断预览页面的父页面是否是发布页面或者预览页面, 如果是的话就不在作品里显示未发布标签
                var pathNames = [
                    '/publish.php',
                    '/client/ha.php',
                    '/anidetail.php'
                ];
                var isDisplay = true;
                if (window.parent) {
                    for (var i = 0; i < pathNames.length; i++) {
                        if (window.parent.location.pathname == pathNames[i]) {
                            isDisplay = false;
                        }
                    }
                }
                if (isDisplay) {
                    findStage();
                }
            })();
        </script>
    </div>
<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//card.mugeda.com/weixin/card/analytics.js','ga');

  ga('create', 'UA-38551434-1', 'auto');
  ga('send', 'pageview');
</script>

</body>
</html>
