# Web Warning

## 1. 表单提交
### 1.1 获取post请求参数
```
<!-- method="POST" POST 必须大写 -->
<form action="http://localhost:8999/hello" method="POST">
    username <input type="text" name="username"/> <br>
    password <input type="text" name="password" /> <br>
    <input type="submit">
</form>

// 需要留意的以下问题
func handle(w http.ResponseWriter, r *http.Request) {
    //	method="POST" post 必须为大写, 否则 r.PostForm is nil 
	r.ParseForm()
	fmt.Fprintln(w, "Form ", r.Form)
	fmt.Fprintln(w, "PostForm", r.PostForm)
}
```
