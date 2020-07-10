## post

```shell
 curl -d "mac=00:11:22:33:44:55&sn=1234567890" http://192.168.83.33/cgi-bin/download.cgi > config.log
 wget --post-data="mac=00:11:22:33:44:55&sn=1234567890" http://192.168.83.33/cgi-bin/confirm.cgi -O config.log
```

## get

```shell
curl http://192.168.83.33/firmware/test.log -o test.log
wget http://192.168.83.33/firmware/test.log
```

## 注册

```mysql
INSERT INTO  DEV_DATA(MAC,SN)
VALUES('00:11:22:33:44:55','1234567890');


select * from web_account where name='admin1';


Method: POST


Length: 24


str: username=aa&password=aaa


curl -d "{\"firstName\": \"John\",\"lastName\": \"Smith\",\"age\": 25}"  http://localhost:30000/string
 
 
 curl -d "{\"firstName\": \"John\",\"lastName\": \"Smith\",\"ttttttttttttttttt\": 25}"  http://localhost:30000/string
 
 curl -d "{\"firstName\": \"John\",\"lastName\": \"Smith\",\"ttttttttttttttttt\": 25}"  https://abdms.aibee.cn/string
 
 
 curl -d "{\"site_id\":\"CTF_beijing_wcc\"}" https://abdms.aibee.cn/CameraStatGet
 
 {
	"site_id":"CTF_beijing_wcc",
	"camera_state_list":[
		{
			"alarm_status":[{"moved":"0"}],
			"ip":"192.168.254.1"
		}
	]
}

curl -d "{\"site_id\": \"CTF_beijing_wcc\",\"camera_state_list\":[{\"ip\": \"192.168.254.1\",\"alarm_status\":[{\"moved\": \"1\"}]}]}" https://abdms.aibee.cn/CameraStatSet
```



## html 语法相关

```html
img 元素具有 alt 属性。alt 属性中的文本用于屏幕阅读器以提高可访问性，并且如果图像无法加载，则会显示。
让我们在上面的 img 示例中添加一个 alt 属性：
<img src="https://www.your-image-source.com/your-image.jpg" alt="your-image">


HTML具有用于创建 unordered lists（无序列表） ，或带项目符号列表的特殊元素。
无序列表以 <ul> 元素开始，并包含一个或多个<li>元素。
例如：

<ul>    
  <li>milk</li>    
  <li>cheese</li>    
</ul>

现在我们来创建一个Web表单。
文本输入框是获取用户输入的一种方便的方法。
你可以用如下方法创建：
<input type="text">
注意，input元素是自关闭的。

placeholder text（占位符）是用户在 input 框输入任何内容之前放置在 input 框中的预定义文本。
你可以创建如下所示的占位符：
<input type="text" placeholder="this is placeholder text">


你可以使用HTML来构建跟服务器交互的Web表单。你可以通过在form元素上添加一个action属性来执行此操作。
action属性的值指定了表单提交到服务器的地址。
例如：
<form action="/url-where-you-want-to-submit-form-data"></form>


<form action="/submit-cat-photo">
    <input type="text" placeholder="cat photo URL">
    <button type="submit">Submit
    </button>
</form>


我们在form中添加一个 submit (提交)按钮。点击此按钮，表单中的数据将会被发送到你使用表单 action 属性指定的地址上。
以下是一个submit按钮的例子：
<button type="submit">this button submits the form</button>

对于表单，你可以指定某些选项为required（必填项），只有当用户填写了该选项后，用户才能够提交表单。
例如，如果你想要一个文本输入框设置为必填项，你可以在 input 元素中加上 required 属性，你可以使用： 
<input type="text" required>
```



