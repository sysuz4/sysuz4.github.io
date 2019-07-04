<h1> 代码规范说明 </h1>

<h2>代码规范的意义和作用 </h2>
<ul>
    <li>编码规范可以最大限度的提高团队开发的合作效率</li>
    <li>编码规范可以改善软件的可读性，可以让开发人员尽快而彻底地理解新的代码</li>
    <li>规范性编码还可以让开发人员养成好的编码习惯，甚至锻炼出更加严谨的思维</li>
    <li>编码规范可以尽可能的减少一个软件的维护成本 , 并且几乎没有任何一个软件，在其整个生命周期中，均由最初的开发人员来维护</li>
</ul>

<h2> 后端代码规范说明 </h2>
<ol>
    <h3><li>项目结构规范</li></h3>
        <ol>
            <h4><li>简述</li></h4>
            一个项目对应代码仓库中的一个仓库，项目结构是指一个基于Maven创建的项目目录结构。公共组件项目，通常会创建一个Maven普通项目。服务组件项目，通常会创建一个Maven聚合项目，并在聚合项目目录下创建多个继承Maven聚合项目的Maven模块，它们一起作为服务组件项目的组成部分。
            <h4><li>项目名</li></h4>
                <ul>
                    <li>要求</li>
                        <ul>
                            <li>英文名称，作为仓库，项目，项目根目录，组件（公共组件，服务组件）的名称</li>
                            <li>中文名称，用于代码仓库的描述</li>
                            <li>项目名称和代码仓库的名称保持一致</li>
                        </ul>
                    <li>定义</li>
                        <ul>
                            <li>项目名称通常由团队负责人确定</li>
                        </ul>
                </ul>
            <h4><li>模块命名</li></h4>
                <ul>
                    <li>要求</li>
                        <ul>
                            <li>模块名称：{项目名称}-{模块名称} 模块名称简洁体现职责</li>
                            <li>模块名字作为模块组件的名称</li>
                        </ul>
                </ul>
            <h4><li>项目目录</li></h4>
                <ul>
                    <li>项目目录遵循Maven约定目录格式</li>
                </ul>
            <h4><li>源码目录</li></h4>
                <ul>
                    <li>源码目录指：{项目目录}/src/main/</li>
                    <li>打包定义目录：src/main/assembly</li>
                    <li>代码目录：src/main/java</li>
                    <li>资源目录：src/main/resources</li>
                        <ul>
                            <li>/db：数据库脚本归档</li>
                            <li>/data：内部依赖数据归档</li>
                        </ul>
                    <li>文档目录：src/main/docs</li>
                    <li>脚本目录：src/main/bin</li>
                        <ul>
                            <li>run-manage.sh 运行管理脚本（通过参数start, stop, status, help info控制程序运行）</li>
                            <li>sh：服务组件启动脚本</li>
                            <li>sh：服务组件停止脚本</li>
                        </ul>
                </ul>
        </ol>
    <h3><li>编码规范</li></h3>
        <ol>
            <h4><li>包规范</li></h4>
                 <ul>
                    <li>项目基本包：com.company.{项目英文名（较长时适当简化）}.{模块名（可选）}</li>
                    <li>config：配置类</li>
                    <li>startup：与服务启动相关的类</li>
                    <li>client：提供客户端实现的相关类</li>
                    <li>common：公共类，定义常量类，组件</li>
                    <li>entity: 数据库相关的实体类</li>
                    <li>model:数据模型类(参数模型，数据传输模型等）</li>
                    <li>control:控制层接口</li>
                    <li>service: 服务层</li>
                    <li>dao：数据库访问层</li>
                </ul>
            <h4><li>日志记录</li></h4>
                <ul>
                    <li>统一使用SLF4j接口</li>
                </ul>
            <h4><li>异常处理</li></h4>
                <ul>
                    <li>运行时异常：通过参数检查等方式避免或抛出运行时异常，日志记录</li>
                    <li>检查异常：检查异常需要捕获，处理，日志记录</li>
                </ul>
            <h4><li>接口定义</li></h4>
                <ul>
                    <li>原则</li>
                        <ul>
                            <li>接口地址定义表明用意</li>
                            <li>接口地址定义清晰，简洁，无歧义</li>
                            <li>同一个服务组件的接口定义具有一致性</li>
                        </ul>
                    <li>格式</li>
                        <ul>
                            <li>控制类的顶层地址格式:/{顶层分类名}，例如：/library 人员库相关接口的顶层地址</li>
                            <li>接口定义使用Swagger的API注解说明</li>
                            <li>标注完整的请求信息，请求方法，请求地址，参数可选性，接口描述</li>
                        </ul>
                    <li>请求方式</li>
                        <ul>
                            <li>GET URL-Params</li>
                            <li>POST Create_Data</li>
                            <li>PUT Modify_Data</li>
                            <li>DELETE Uer_Data</li>
                        </ul>
                    <li>响应方式</li>
                        <ul>
                            <li>统一的响应模型</li>
                        </ul>
                </ul>
            <h4><li>辅助工具</li></h4>
                <ul>
                    <li>字符串处理：apache common-lang3</li>
                    <li>时间日期处理：joda-time</li>
                    <li>JSON处理：Gson，Fastjson</li>
                    <li>集合扩展工具：guava</li>
                    <li>文件和流处理：commons-io</li>
                    <li>编解码：commons-codec</li>
                    <li>建议：尽可能使用开源组件</li>
                </ul>
            <h4><li>代码注释</li></h4>
                <ul>
                    <li>类，接口，枚举顶层注释</li>
                    <li>接口方法注释</li>
                    <li>静态方法注释</li>
                    <li>公开方法注释</li>
                    <li>类的属性字段注释</li>
                    <li>常量注释</li>
                    <li>不限于以上</li>
                </ul>
        </ol>
    <h3><li>代码控制规范</li></h3>
        <ol>
            <h4><li>拉取原则</li></h4>
                <ul>
                    <li>强制</li>
                        <ul>
                            <li>每日开始工作拉取</li>
                        </ul>
                    <li>约定</li>
                        <ul>
                            <li>提交之前拉取</li>
                        </ul>
                </ul>
            <h4><li>提交原则</li></h4>
                <ul>
                    <li>强制</li>
                        <ul>
                            <li>提交代码必须构建成功（比如：编译，打包成共）</li>
                            <li>提交代码必须完整（比如：少提文件）</li>
                            <li>提交代码必须忽略到本地临时文件（比如：target, logs, .idea, *.iml,dist 等）</li>
                        </ul>
                    <li>约定</li>
                        <ul>
                            <li>完成一个功能提交</li>
                            <li>修改一个Bug修改提交</li>
                            <li>解决冲突提交</li>
                            <li>每日结束工作提交</li>
                        </ul>
                </ul>
            <h4><li>提交注释</li></h4>
                <ul>
                    <li>强制</li>
                        <ul>
                            <li>中文填写注释</li>
                            <li>注释反映本次提交变更情况</li>
                        </ul>
                    <li>约定</li>
                        <ul>
                            <li>注释描述添加前缀，前缀如下</li>
                            <li>[创建] 通常在项目创建时使用</li>
                            <li>[新增]</li>
                            <li>[修改]</li>
                            <li>[删除]</li>
                            <li>[修复-number] 修复Bug使用，number是Bug编号</li>
                        </ul>
                </ul>
        </ol>
    <h3><li>构建规范</li></h3>
        <ol>
            <h4><li>公共组件构建规范</li></h4>
                <ul>
                    <li>构建输出组件包</li>
                    <li>构建输出组件源码包</li>
                    <li>构建发布到公司私有仓库</li>
                </ul>
            <h4><li>服务组件构建规范</li></h4>
                <ul>
                    <li>服务组件包命名：{组件名称}-{版本号}-bin.zip</li>
                    <li>构建输出到工程根目录下的dist/{组件名称}-{yyyyMMddHH}目录</li>
                </ul>
        </ol>
</ol>
<h2> 前端代码规范说明 </h2>
    <ol>
        <h3><li>设计原则</li></h3>
            <ul>
                <li>逻辑代码独立到单独的方法中，注重封装性--易读，易复用。不要在一个方法中，写下上百行的逻辑代码。把各小逻辑代码独立出来，写于其它方法中，易读其可重复调用。</li>
                <li>写类，写方法，写功能时，应考虑其移植性，复用性：防止一次性代码！</li>
                <li>熟练运用继承的思想： 找出应用中相同之处，且不容易发生变化的东西，把它们抽取到抽象类中，让子类去继承它们；继承的思想，也方便将自己的逻辑建立于别人的成果之上</li>
                <li>熟练运用接口的思想：找出应用中可能需要变化之处，把它们独立出来，不要和那些不需要变化的代码混在一起。</li>
            </ul>
        <h3><li>命名规范</li></h3>
            <table>
                <tr>
                    <td>类型</td>
                    <td>规则</td>
                    <td>示例</td>
                </tr>
                <tr>
                    <td>Activity</td>
                    <td>XxxxActivity</td>
                    <td>MainActivity</td>
                </tr>
                <tr>
                    <td>View</td>
                    <td>XxxView，XxxLayout</td>
                    <td>RedTextView、BluetoothDialog</td>
                </tr>
                <tr>
                    <td>Service</td>
                    <td>XxxService</td>
                    <td></td>
                </tr>
                <tr>
                    <td>BroadcastReceiver</td>
                    <td>XxxxReceiver</td>
                    <td></td>
                </tr>
                <tr>
                    <td>工具方法类</td>
                    <td>Utils或Manager为后缀</td>
                    <td>ThreadPoolManager、LogUtils</td>
                </tr>
                <tr>
                    <td>基础类</td>
                    <td>BaseXxx</td>
                    <td>aseActivity、BaseFragment、BaseDao</td>
                </tr>
                <tr>
                    <td>布局xml</td>
                    <td>全部小写，以下划线分割，使用名词命名。Activity或Fragment的布局文件必须与其类名对应，对应规则为：将所有字母都转为小写，将类型和功能调换。</td>
                    <td>activity_main.xml
                        fragment_homework.xml
                        dialog_bluetooth.xml //对话框
                        item_message.xml //列表Item
                        vw_titlebar.xml //其他布局文件</td>
                </tr>
                <tr>
                    <td>布局id</td>
                    <td>全部小写，以下划线分割，view缩写_view的逻辑名称</td>
                    <td>layout_city、tv_name、btn_submit、img_head、list_message</td>
                </tr>
                <tr>
                    <td>图片文件</td>
                    <td>全部小写，以下划线分割。</td>
                    <td>xxxx_checked.png
                        xxxx_focused.png
                        xxxx_selected.png
                        xxxx_pressed.png
                        xxxx_disabled.png
                        xxxx_normal.png</td>
                </tr>
                <tr>
                    <td>Drawable xml</td>
                    <td>selector_xxx、shape_xxx</td>
                    <td></td>
                </tr>
            </table>
        <h3><li>注释</li></h3>
            <ol>
                <li>每个类必须有文件头注释。简要说明类的作用，注明作者和创建时间。标准模板：</li>
                    /**   <br>
                    * Filedescription.<br>
                    *<br>
                    * @author ${USER}<br>
                    * @date ${DATE}<br>
                    *
                <li>大部分方法都需要方法注释，一些不言自明的方法除外。简要说明方法作用，并解释参数、返回值、抛出异常。方法注释请使用JavaDoc标准。例如：</li>
                    /**<br>
                    * Description.<br>
                    *<br>
                    * @param arg1 description<br>
                    * @param arg2 description<br>
                    * @return description<br>
                    * @throws Exception description<br>
                    */<br>
                    public int getFoo(int arg1, booleanarg2) throws Exception {<br>
                    &emsp;&emsp;return 0;<br>
                    }<br>
                <li>关键逻辑或者较复杂的逻辑处，应该添加必要的注释。单行注释使用”//”，多行注释使用/**/。</li>
                <li>注释必须在程序改变时实时更新。</li>
                <li>简单明了，确保任何程序员都可以读懂。</li>
            </ol>
        <h3><li>提高代码质量</li></h3>
            <ul>
                <li>删除无用的变量</li>
                <li>删除无用的引入 </li>
                <li>对于可以复用的部分，一定提取成共用的方法，减少代码量</li>
                <li>变量/方法命名一定要符合清晰易懂，不用太在乎长度</li>
                <li>代码完成后，进行code review，减少出错几率 </li>
                <li>用适合的方式尽量去思考设计模式方式来进行开发</li>
            </ul>
        <h3><li>其他规范</li></h3>
            <ul>
                <li>所有文件编码格式为UTF-8。</li>
                <li>变量的作用域应该尽量小，需要时才声明，并尽快进行初始化。</li>
                <li> 前大括号不要单独占用一行，不要省略单行代码块的大括号。</li>
                正确：<br>
                if (condition) {<br>
                &emsp;&emsp;statements;<br>
                }<br>
                错误：<br>
                if (condition)  //没有大括号<br>
                &emsp;&emsp;statement;<br>
                错误：<br>
                if (condition)  //前大括号单独占用一行<br>
                {<br>
                &emsp;&emsp;statement;<br>
                }<br>
                <li>尽量少使用缩写，除非该缩写很常见（Html、Url）</li>
                <li>缩进使用4个空格替代Tab。</li>
                <li>编写代码后必须格式化。AndroidStudio默认格式化快捷键：Ctrl+Alt+L。</li>
                <li>在代码中逻辑性代码块的起始、结尾处，都应该加入空行，并在起始处写注释。相对独立的程序块之间必须加空行。</li>
                <li>一行代码不超过150字符。超过150字符，请换行或者提取变量。</li>
                <li>方法体不超过100行。若超过，则应考虑拆分成多个方法。</li>
                <li>尽量避免使用枚举类，使用常量代替。</li>
                <li>只要是合法的，就把@Override注解给用上。</li>
                <li>规范TODO使用，加上日期和描述，并及时解决删除。AndroidStudio中可以敲todo来使用标准模板。例如：
                // TODO: 2017/1/5简单描述</li>
                <li>采用统一的LogUtils来输出Log。输出的Log要简明扼要。充足的log可以便于定位错误，但Log太多会影响程序性能(I/O耗时)。正式版本应该关闭Log开关。</li>
                <li>Java文件中不允许有多余的import，不允许importjava.io. *</li>
                <li>Warning要解决。</li>
                <li>不允许硬编码，状态值必须定义常量，并添加注释。</li>
            </ul>
    </ol>
