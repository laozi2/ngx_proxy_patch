# ngx_proxy_patch

### 说明

+ nginx http proxy 模块发起的请求不支持将地址放到请求行里， 这里做个patch, 达到效果

  ```
  GET http://abc.com/test HTTP/1.1
  ```

  即增加 `http://abc.com`



### 版本

+ nginx-1.10.3


### 打补丁

+ 编译安装之前

  ```
  在nginx-1.10.3目录下:
  将 ngx_http_proxy_module.patch 放到当前目录，执行
  patch -p1 < ngx_http_proxy_module.patch 
  ```



### 用法

+ 在代理location加上 `set $proxy_req_line "http://abc.com";`, 例如

  ```
  location / {
      set $proxy_req_line "http://abc.com";
      proxy_pass http://abc.com/;
  }
  ```
