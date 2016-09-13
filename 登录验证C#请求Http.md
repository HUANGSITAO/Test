# 登录验证 #
## 问题描述 ##
使用C#发送Post请求返回一个json字符串，解析字符串使之变成C#可用对象格式。</br>
调用
<pre><code>PostRequest("http://bbeitv.com/vr/get-rtmp",username.Text,password.Password);
</code></pre>
函数实现
<pre><code>
async static void PostRequest(string url,string username,string password)
{
    IEnumerable<KeyValuePair<string, string>> queries = new List<KeyValuePair<string, string>>()
    {
        new KeyValuePair<string,string>("username",/*"1385717333"*/username),
        new KeyValuePair<string,string>("password",/*"admins"*/password)
    };

    HttpContent q = new FormUrlEncodedContent(queries);
    using (HttpClient client = new HttpClient())
    {
        using (HttpResponseMessage response = await client.PostAsync(url, q))
        {
            using (HttpContent content = response.Content)
            {
                string mycontent = await content.ReadAsStringAsync();
                HttpContentHeaders headers = content.Headers;
		//返回字符串格式外面加上@[]
                string str = @"[";
                str += mycontent;
                str += "]";
                //引用Newtonsoft.Json库，并using
                List<Result> res = JsonConvert.DeserializeObject<List<Result>>(str);
                foreach (var item in res)
                {
                    if (item.code == 200) {
                        MessageBox.Show("登录成功");
                        isLogin = true;
                    }
                    else if (item.code == 500) {
                        MessageBox.Show(item.message);
                        isLogin = false;
                    }
                   // Console.WriteLine("{0},{1}", item.code, item.message);
                }
                System.Windows.MessageBox.Show(mycontent);

            }
        }

    }
}
</code></pre>
定义和返回的json相同格式类
<pre><code>
public class Result
{
    public int code { get; set; }
    public string message { get; set; }
    public data data { get; set; }
}
public class data { 
   public string username { get; set; }
   public string nickname { get; set; }
   public string bbid { get; set; }
   public string live_title { get; set; }
   public string rtmp { get; set; }
   public string http { get; set; }
}
</code></pre>