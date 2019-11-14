# Отключить работу c iframe для webvisor 

## Для nginx

Закомментировать строчку
```
add_header X-Frame-Options SAMEORIGIN;
```

В блок location ~/$
```
set $frame_options '';
if ($http_referer !~ '^https?:\/\/([^\/]+\.)?(webvisor\.com)\/'){
    set $frame_options 'SAMEORIGIN';
}
add_header X-Frame-Options $frame_options;
```