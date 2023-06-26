

# 机器人的webhook地址
```shell script
curl 'https://qyapi.weixin.qq.com/cgi-bin/webhook/send?key=9a5d8dc2-7623-468d-b438-563e6e7920bb' \
   -H 'Content-Type: application/json' \
   -d '
   {
    	"msgtype": "text",
    	"text": {
        	"content": "hello world"
    	}
   }'
```
-H： “Content-type: application/json” 添加 HTTP 请求头 curl -H 'Content-type: application/json' $url

-d： 发送post请求数据
