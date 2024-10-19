## ElementUL
    标签
        ## <el-row :gutter=''>  // 栅格间距
                <el-col :span='24'></el-col>  // 平分
            </el-row>

        ## el-card

        ## dr  //下拉菜单
            <el-dropdown >
                <i class="el-icon-more"></i>
                <el-dropdown-menu slot="dropdown">
                    <el-dropdown-item>黄金糕</el-dropdown-item>
                    <el-dropdown-item>狮子头</el-dropdown-item>
                    <el-dropdown-item>螺蛳粉</el-dropdown-item>
                    <el-dropdown-item>双皮奶</el-dropdown-item>
                    <el-dropdown-item>蚵仔煎</el-dropdown-item>
                </el-dropdown-menu>
            </el-dropdown>


        ## button
            type=""  类型  primary/success/warning/danger/info/text
            icon=""  图标
            disabled  是否禁用

        ## input
            type=""  text、textarea和其他原生input的type值
            placeholder=""  占位符
            label=""  输入框关联的label文字

            event:
                blur	失去焦点时触发	(event: Event)
                focus	获得焦点时触发	(event: Event)
                change	仅在输入框失去焦点或用户按下回车时触发	(value: string | number)
                input	值改变时触发	(value: string | number)

            methods:
                focus	获取焦点
                blur	失去焦点
                select	中的文字

        ## table
            data=""  绑定的数据
            border  纵向边框

            table-column  
                type=""
                    selection  多选框
                index索引
                expand展开的按钮
                lable显示的标题
                prop对应列的内容(与data绑定)
                width对应列宽度
                align对齐方式

            <template slot-scope="{row, column, $index}">  // table-column作用域插槽
                {{ row }}
            </template>

        ## form
            model表单数据对象
            rules表单验证
            .validate检验校验是否通过
            inline行内表单

            form-item  //prop收集数据绑定对象、label标签文本、required是否必填


        ## upload  //action上传地址、show-file-list是否显示已上传文件列表:on-success=""上传成功回调、:before-upload=""上传之前回调
        
        ## dialog  //对话框  title标题、visible是否显示
    
    方法
        $message  //({type: success/warning/info/error, message: '提示信息'})
        messageBox
            $msgbox(options)  //自定义
            $alert(message, title, options)  //消息提示
            $confirm(message, title, options)  //确认消息
            $prompt(message, title, options)  //提交内容
                message消息内容、title标题、options{
                    confirmButtonText: '确定',
                    cancelButtonText: '取消',
                    type: 'warning'
                }
                .then()  //点击确定回调
                .catch()  //点击取消回调

        pagination  //分页器
            :current-page="page"当前页数
            page-size每页显示数据条数
            total数据总条数
            page-count分页器总页数
            pager-count页码按钮数量
            layout="prev, pager, next, jumper, sizes, total"  //组件布局
            :page-sizes="[3, 5, 10]"  //每页显示数量设置
            @current-change=""当前页数发生改变的回调
            @size-change=""  展示数据条数发生改变的回调