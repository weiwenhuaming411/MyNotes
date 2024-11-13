## HTML
    <!DOCTYPE html>
    <html lang="en">
        <head>
            <meta charset="UTF-8">  // 描述HTML文档的描述，关键词，作者，字符集等
            <meta http-equiv="X-UA-Compatible" content="IE=edge">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">  // 移动端适配
            <title>Document</title>  // 标题
            <link rel="stylesheet" href="../index.css">  // 引入外部资源
            <style></style>  // 样式
            <base>  // 定义页面中所有链接默认的链接目标地址
        </head>
        <body>
            <!-- 注释 -->
            <script></script>  // 定义了客户端脚本
            <noscript></noscript>  // 定义了不支持脚本浏览器输出的文本
        </body>
    </html>
    
## 标签:
    <!-- input输入框 -->
        <input type="text">  
            name=''  元素名称
            value=''  指定默认值
            disabled  禁止
            readonly  设置为只读
            maxlength=''  最长字符
            autofocus  // 自动获取焦点
            placeholder  // 占位符
            required  // 必填
            
            from='formId'  规定所属哪个表单
            size=''  可见宽度
            autocomplete  // 自动填充 on/off
            list='age'  配合预选列表使用
                <!-- <datalist>预选列表 -->
                    <input type="text" list="age">
                    <datalist id="age">
                        <option value="男">男</option>
                        <option value="女">女</option>
                    </datalist>

            type=''
                text
                password
                number  // step规定数字间隔
                radio|checkbox  // checked获取选装状态
                file上传文件  // accept='audio|video|image' 规定文件类型 multiple 允许上传多个文件
                image显示图片 // src='' alt='' 图像提交文本 width='' height=''
            
    <!-- <label></label> -->  
        <label for="man">男</label>  // 标注input输入框,关联表单(id)元素
        <input type="radio" id="man" name="age" value="男">
    
    <!-- form表单 -->
        <form>
            name=''
            action='url'  发送请求
            method=''  请求类型
            enctype=''  规定发送表单数据之前对其进行编码
                application/x-www-form-urlencoded  // 默认值
                multipart/form-data  // 
                text/plain  // 
        </form>

    <!-- select下拉菜单 -->
        <select>
            <optgroup label="German Cars">  // 定义选项组
                <option value="mercedes">Mercedes</option>  // 下拉选项
                <option value="audi">Audi</option>
            </optgroup>
            <option value="mercedes">Mercedes</option>
                属性:
                    disabled  规定此选项应在首次加载时被禁用。
                    label  定义当使用 <optgroup> 时所使用的标注。
                    selected  规定选项（在首次显示在列表中时）表现为选中状态。
                    value  定义值
        </select>
            属性:
                autofocus  规定在页面加载时下拉列表自动获得焦点
                disabled  当该属性为 true 时，会禁用下拉列表
                multiple  当该属性为 true 时，可选择多个选项
                required  规定用户在提交表单前必须选择一个下拉列表中的选项
                size  规定下拉列表中可见选项的数目

    <!-- textarea文本域 -->
        <textarea></textarea>
            name  // 规定文本区域的名称
            autofocus  // 规定当页面加载时，文本区域自动获得焦点
            cols="number"  // 规定文本区域内可见的宽度
            rows="number"  // 规定文本区域内可见的行数
            disabled  // 规定禁用文本区域
            form  // 定义文本区域所属的一个或多个表单
            maxlength="number"  // 规定文本区域允许的最大字符数
            placeholder="text"  // 规定一个简短的提示，描述文本区域期望的输入值。
            readonly  // 规定文本区域为只读。
            required  // 规定文本区域是必需的/必填的
            wrap="hard/soft"  // 规定当提交表单时，文本区域中的文本应该怎样换行
                
    <!-- table表格 -->
        <table border='1'>
            <tr>  // 行
                <th colspan='2'横跨列数 rowspan='2'纵跨行数></th>  // 表头
                <td></td>  // 内容
            </tr>
        </table>

### HTML5 音频/视频 DOM 参考手册API
    https://www.runoob.com/tags/ref-av-dom.html

    <!-- 音频 -->
    <audio
        src
        autoplay 自动播放
        controls 音频控件
        loop 循环播放
        muted 静音
        preload='auto|metadata|none' 规定当网页加载时，音频是否默认被加载以及如何被加载。
    >
        <source src="horse.mp3" type="audio/mpeg|audio/ogg|audio/wav"> 多文件配置
    </audio>

    <!-- 视频 -->
    <video
        width="320"
        height="240"
        poster="./public/347075.jpg"  主界面图
    >
        <track></track> // 定义在媒体播放器文本轨迹(字幕)
        <source src="movie.mp4" type="video/mp4|video/webm|video/ogg">
    </video>

    属性:
        src  设置或返回音频/视频元素的当前来源  url
        currentSrc  返回当前音频/视频的URL  url
        autoplay  设置或返回是否自动播放  true/false
        loop  设置或返回是否循环播放  true/false
        controls  设置或返回是否显示控件  true/false
        paused  设置或返回是否暂停  true/false
        muted  设置或返回是否静音  true/false
        defaultMuted  设置或返回默认是否静音  true/false
        volume  设置或返回音量  number
        playbackRate  设置或返回播放的速度  number
        defaultPlaybackRate  设置或返回默认播放速度  number
        duration  返回当前音频/视频的长度（以秒计）  number
        currentTime  设置或返回音频/视频中的当前播放位置（以秒计）  number
        ended  返回音频/视频的播放是否已结束  true/false
        seeking  返回用户是否正在移动/跳跃到音频/视频中的新位置  true/false

        preload  设置或返回音频/视频是否应该在页面加载后进行加载
            auto  指示一旦页面加载，则开始加载音频/视频
            metadata  指示当页面加载后仅加载音频/视频的元数据
            none  指示页面加载后不应加载音频/视频
        readyState  返回音频/视频当前的就绪状态
            0 = HAVE_NOTHING - 没有关于音频/视频是否就绪的信息
            1 = HAVE_METADATA - 关于音频/视频就绪的元数据
            2 = HAVE_CURRENT_DATA - 关于当前播放位置的数据是可用的，但没有足够的数据来播放下一帧/毫秒
            3 = HAVE_FUTURE_DATA - 当前及至少下一帧的数据是可用的
            4 = HAVE_ENOUGH_DATA - 可用数据足以开始播放
        mediaGroup  设置或返回音频/视频所属的组合（用于连接多个音频/视频元素）  ?
            audio.mediaGroup = 'text'
        networkState  返回音频/视频的当前网络状态  1
            0 = NETWORK_EMPTY - 音频/视频尚未初始化
            1 = NETWORK_IDLE - 音频/视频是活动的且已选取资源，但并未使用网络
            2 = NETWORK_LOADING - 浏览器正在下载数据
            3 = NETWORK_NO_SOURCE - 未找到音频/视频来源
        crossOrigin  设置或返回音频/视频的 CORS 设置  ?
        seekable  返回表示音频/视频可寻址部分的 TimeRanges 对象
            length - 获得音频/视频中可寻址范围的数量
            start(index-1) - 获得可寻址范围的开始位置
            end(index-1) - 获得可寻址范围的结束位置
        played  返回表示音频/视频已播放部分的 TimeRanges 对象
            let index = audio.played.length
            audio.played.length  // 获得音频/视频中已播范围的数量
            audio.played.start(index-1)  // 获得某个已播范围的开始位置
            audio.played.end(index-1)  // 获得某个已播范围的结束位置
        buffered  返回表示音频/视频已缓冲部分的 TimeRanges 对象
            length - 获得音频/视频中已缓冲范围的数量
            start(index) - 获得某个已缓冲范围的开始位置
            end(index) - 获得某个已缓冲范围的结束位置
        textTracks  返回表示可用文本轨道的 TextTrackList 对象
            TextTrackList 对象	表示音频/视频的可用文本轨道。
                length - 获得音频/视频中可用的文本轨道的数量
                [index] - 根据下标 index 来获得 TextTrack 对象
                注释：第一个可用文本轨道的下标 index 是 0。
            TextTrack 对象	表示一个文本轨道
                kind - 获得文本轨道的类型（可以是 "subtitles"、"caption"、"descriptions"、"chapters" 或者 "metadata"）
                label - 获得文本轨道的标签
                language - 获得文本轨道的语言
                mode - 获得或设置该轨道是否是活动的（"disabled"|"hidden"|"showing"）
                cues - 获得 TextTrackCueList 对象的 cues 列表
                activeCues - 获得 TextTrackCueList 对象形式的当前活动文本轨道 cues
                addCue(cue) - 向 cues 列表添加一个 cue
                removeCue(cue) - 从 cues 列表删除一个 cue

        error  返回表示音频/视频错误状态的 MediaError 对象  (只有IE9支持)
            audio.error.code
        
    方法:
        audio.play()  // 播放媒介
        audio.pause() // 暂停播放媒介
        audio.load()  // 重新加载媒介
        addTextTrack()  // 向音频/视频添加新的文本轨道
        canPlayType()  // 检测浏览器是否能播放指定的音频/视频类型。

    事件:
        // 提示视频已开始加载
        audio.onloadstart = ()=>{console.log('loadstart')}
        // 提示视频的时长已改变（NaN→实际时长）
        audio.ondurationchange = ()=>{console.log('durationchange')}
        // 提示视频的元数据已加载
        audio.onloadedmetadata = ()=>{console.log('loadedmetadata')}
        // 提示当前帧的数据是可用的
        audio.onloadeddata = ()=>{console.log('loadeddata')}
        // 提示视频正在下载中
        audio.onprogress = ()=>{console.log('progress')}
        // 提示该视频已准备好开始播放
        audio.oncanplay = ()=>{console.log('canplay')}
        // 提示视频能够不停顿地一直播放
        audio.oncanplaythrough = ()=>{console.log('canplaythrough')}

        onplay  当音频/视频已开始或不再暂停时触发
        onpause  当音频/视频已暂停时触发
        onvolumechange  当音量已更改时触发
        onratechange  当音频/视频的播放速度已更改时触发
        ontimeupdate  当目前的播放位置已更改时触发

        onplaying  当音频/视频在因缓冲而暂停或停止后已就绪时触发
        onwaiting  当视频由于需要缓冲下一帧而停止时触发
        onseeking  当用户开始移动/跳跃到音频/视频中的新位置时触发
        onseeked  当用户已移动/跳跃到音频/视频中的新位置时触发
        
        onended  当目前的播放列表已结束时触发
        onemptied  当目前的播放列表为空时触发

        onabort  当音频/视频的加载已放弃时触发
        onsuspend  当浏览器刻意不获取媒体数据时触发

        onstalled  当浏览器尝试获取媒体数据，但数据不可用时触发
        onerror  当在音频/视频加载期间发生错误时触发
        
        onreadystatechange  当就绪状态（ready-state）改变时运行脚本
        onseeked  当媒介元素的定位属性 [1] 不再为真且定位已结束时运行脚本

### canvas图形
    https://www.runoob.com/html/html5-canvas.html
    https://www.runoob.com/tags/ref-canvas.html

### SVG可缩放矢量图形
    https://www.runoob.com/html/html5-svg.html

### 地图
    https://www.runoob.com/html/html5-geolocation.html

### 字符集
    https://www.runoob.com/charsets/html-charsets.html
        <  &lt;  
        >  &gt;

### 拖放
    https://www.runoob.com/html/html5-draganddrop.html