# awesome-condor-api
A simple lightweight API 

* [Controller](#controller)
* [Request](#request)

## Controller
```objc
//controller.php 
<?php

public function add(RequestAdd $request, Service $service, $array_datas)
{
    $response = $service->Add($array_datas);
    return $response
}
public function get(RequestGet $request, Service $service)
{
  $response = $service->get($array_datas);
    return $response
}
public function put(RequestPut $request, Service $service)
{
  $response = $service->put($array_datas);
    return $response
}
public function remove(RequestRemove $request, Service $service)
{
  $response = $service->remove($array_datas);
    return $response
}
```
## Request
```objc
//request.php
```
