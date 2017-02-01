# annotated_nginx
Annotated Nginx Source（中文）

# 简介
Nginx源码分析，注解代码，帮助学习Nginx。

当前使用的是1.10.3稳定版。

Nginx1.10增加了动态模块、http2、reuseport。

Nginx1.11.x里的stream模块的变动较大，完善了阶段处理，待1.12发布后即可详细注解。

请参考：
* [《Nginx模块开发指南：使用C++11和Boost程序库》](http://item.jd.com/11785180.html)
* [ngx_cpp_dev](https://github.com/chronolaw/ngx_cpp_dev)
* [openresty_dev](https://github.com/chronolaw/openresty_dev)
* [favorite-nginx](https://github.com/chronolaw/favorite-nginx)
* [stream lua, with log_by_lua/filter_by_lua](https://github.com/chronolaw/stream-lua-nginx-module)

# 当前状态
nginx 1.10.3

# Git分支
分支    |说明   |注释
--------|-------|-----
master  | nginx稳定版1.10.3|有
upgrade | nginx稳定版1.10.3|无
mainline| nginx开发版1.11.8|无

# 已注解

###源码目录快捷入口
* [src](/nginx/src/) - nginx源码目录
* [core](/nginx/src/core) - 60%，md5/sha1/crc等较简单的功能不关注
* [event](/nginx/src/event) - 90%，只注解核心模块和epoll，select/kqueue/ssl等不关注
* [http](/nginx/src/http) - 50%，modules目录里的具体功能模块暂不关注
* [os/unix](/nginx/src/os/unix) - 80%，bsd/darwin/solaris等系统不关注
* [stream](/nginx/src/stream) - 70%

####UML图解
[UML图示](/diagrams/readme.md)

####部分关键源码（目录分类）

######core目录
* [nginx.c](/nginx/src/core/nginx.c)
* [ngx_conf_file.h](nginx/src/core/ngx_conf_file.h)
* [ngx_module.h](nginx/src/core/ngx_module.h)
* [ngx_module.c](nginx/src/core/ngx_module.c)
* [ngx_connection.h](/nginx/src/core/ngx_connection.h)
* [ngx_connection.c](/nginx/src/core/ngx_connection.c)
* [ngx_thread_pool.h](/nginx/src/core/ngx_thread_pool.h)
* [ngx_thread_pool.c](/nginx/src/core/ngx_thread_pool.c)

######event目录
* [ngx_event.h](/nginx/src/event/ngx_event.h)
* [ngx_event.c](/nginx/src/event/ngx_event.c)
* [ngx_event_accept.c](/nginx/src/event/ngx_event_accept.c)
* [ngx_event_timer.c](/nginx/src/event/ngx_event_timer.c)
* [ngx_epoll_module.c](/nginx/src/event/modules/ngx_epoll_module.c)

######http目录
* [ngx_http.h](/nginx/src/http/ngx_http.h)
* [ngx_http.c](/nginx/src/http/ngx_http.c)
* [ngx_http_core_module.h](/nginx/src/http/ngx_http_core_module.h)
* [ngx_http_core_module.c](/nginx/src/http/ngx_http_core_module.c)
* [ngx_http_request.h](/nginx/src/http/ngx_http_request.h)
* [ngx_http_request.c](/nginx/src/http/ngx_http_request.c)
* [ngx_http_request_body.c](/nginx/src/http/ngx_http_request_body.c)
* [ngx_http_header_filter_module.c](/nginx/src/http/ngx_http_header_filter_module.c)
* [ngx_http_write_filter_module.c](/nginx/src/http/ngx_http_write_filter_module.c)

######os/unix目录
* [ngx_os.h](/nginx/src/os/unix/ngx_os.h)
* [ngx_process.c](/nginx/src/os/unix/ngx_process.c)
* [ngx_process_cycle.c](/nginx/src/os/unix/ngx_process_cycle.c)
* [ngx_writev_chain.c](/nginx/src/os/unix/ngx_writev_chain.c)

######stream目录
* [ngx_stream.h](/nginx/src/stream/ngx_stream.h)
* [ngx_stream.c](/nginx/src/stream/ngx_stream.c)
* [ngx_stream_core_module.c](/nginx/src/stream/ngx_stream_core_module.c)
* [ngx_stream_handler.c](/nginx/src/stream/ngx_stream_handler.c)

####部分关键源码（功能分类）

######数据结构
* [ngx_array.h](/nginx/src/core/ngx_array.h)
* [ngx_list.h](/nginx/src/core/ngx_list.h)
* [ngx_string.h](/nginx/src/core/ngx_string.h)
* [ngx_buf.h](/nginx/src/core/ngx_buf.h)
* [ngx_rbtree.h](/nginx/src/core/ngx_rbtree.h)

######进程机制
* [nginx.c](/nginx/src/core/nginx.c)
* [ngx_conf_file.h](nginx/src/core/ngx_conf_file.h)
* [ngx_module.h](nginx/src/core/ngx_module.h)
* [ngx_module.c](nginx/src/core/ngx_module.c)
* [ngx_process.c](nginx/src/os/unix/ngx_process.c)
* [ngx_process_cycle.c](nginx/src/os/unix/ngx_process_cycle.c)

######事件机制
* [ngx_connection.h](/nginx/src/core/ngx_connection.h)
* [ngx_connection.c](/nginx/src/core/ngx_connection.c)
* [ngx_event.h](/nginx/src/event/ngx_event.h)
* [ngx_event.c](/nginx/src/event/ngx_event.c)
* [ngx_event_accept.c](/nginx/src/event/ngx_event_accept.c)
* [ngx_event_timer.c](/nginx/src/event/ngx_event_timer.c)
* [ngx_epoll_module.c](/nginx/src/event/modules/ngx_epoll_module.c)

######多线程机制
* [ngx_event.h](/nginx/src/event/ngx_event.h)
* [ngx_event.c](/nginx/src/event/ngx_event.c)
* [ngx_thread_pool.h](/nginx/src/core/ngx_thread_pool.h)
* [ngx_thread_pool.c](/nginx/src/core/ngx_thread_pool.c)

######tcp(stream)处理
* [ngx_connection.h](/nginx/src/core/ngx_connection.h)
* [ngx_connection.c](/nginx/src/core/ngx_connection.c)
* [ngx_stream.h](/nginx/src/stream/ngx_stream.h)
* [ngx_stream.c](/nginx/src/stream/ngx_stream.c)
* [ngx_stream_core_module.c](/nginx/src/stream/ngx_stream_core_module.c)
* [ngx_stream_handler.c](/nginx/src/stream/ngx_stream_handler.c)

######http处理
* [ngx_connection.h](/nginx/src/core/ngx_connection.h)
* [ngx_connection.c](/nginx/src/core/ngx_connection.c)
* [ngx_http.h](/nginx/src/http/ngx_http.h)
* [ngx_http.c](/nginx/src/http/ngx_http.c)
* [ngx_http_core_module.h](/nginx/src/http/ngx_http_core_module.h)
* [ngx_http_core_module.c](/nginx/src/http/ngx_http_core_module.c)
* [ngx_http_request.h](/nginx/src/http/ngx_http_request.h)
* [ngx_http_request.c](/nginx/src/http/ngx_http_request.c)
* [ngx_http_request_body.c](/nginx/src/http/ngx_http_request_body.c)
* [ngx_http_header_filter_module.c](/nginx/src/http/ngx_http_header_filter_module.c)
* [ngx_http_write_filter_module.c](/nginx/src/http/ngx_http_write_filter_module.c)

# 不注解

* auto
* mail
* misc
