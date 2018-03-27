# awesome-condor-api
A simple lightweight API 

* [Controller](#controller)
* [ControllerSources](#controller-sources)
* [Rules](#rules)
* [Interface](#interface)
* [Repository](#repository)
* [Service](#service)

## Controller
```objc
//controller.php 
<?php

public function add(RulesAdd $request, Service $service, $array_datas)
{
    $response = $service->Add($array_datas);
    return $response
}
public function get(RulesGet $request, Service $service)
{
  $response = $service->get($array_datas);
    return $response
}
public function put(  RulesPut, Service $service)
{
  $response = $service->put($array_datas);
    return $response
}
public function remove(RulestRemove $request, Service $service)
{
  $response = $service->remove($array_datas);
    return $response
}
```
## Controller Sources
```objc
//controllerSources.php
```
class controllerSources()
{
    private $name_source;
    private $method_source;
    //METHODS TO ADD NEW SOURCES
    [...]
    
    //Method to be overrided by child classes
    //because each Source has to be your own method
    public function generic_method($params)
    {
          $this->getMethod_source();  
    }
    //GETTER AND SETTER METHODS
    [...]
}
//source_goole_analytics.php

class source_google_analytics extends controllerSources
{
    $object_controller = new controllerSources();
    $response = $object_controller->Send();
    [...]
    
    return json_encode($response);
}

## Rules
```objc
public function RulesAdd(){}
RulesGet (){}
RulesPut(){}
RulesRemove(){}
```

## Interface
```objc
Interface ServiceInterface
[...]
//ALL METHODS USED IN Services.php
```

## Repository
```objc
//repository.php
[...]
//ALL METHODS USED TO CRUD DATA TO SERVICES.PHP
```

## Service
```objc
// services.php
[...]
class service implements ServiceInterface
{
  private $repository;
    public function __construct(Repository $repository)
    {
        // NOW I HAVE ALL METHODS DO CRUD MY API 
        $this->repository = $repository;
    }
    
    public function get_sources()
    {
        $result = array();
        try{
        $result  = $this->repository->get_sources($array_value);
          if ($result['success'])
          {
            $result["error"] = false;
            $result["message"] = ""
            $result["data"] = array ("Google Analytics" => $result['value'], "Positive Guys" => $result['positiveGuys'];
            
           
          }else
          {
             $result["error"] = true;
             $result["message"] = "OH now something got wrong"
          }
            
         return json_encode($result);
         }
        catch(Exception $e){
          
            return $e->getMessage();

        }
    }
    
    
}


```















