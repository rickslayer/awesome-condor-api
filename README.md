# awesome-condor-api
A simple lightweight API 

**This project is designed as infrastructure rather than fully fleshed application. Your implementation should just show the process you would follow and the architecture you would implement. You are welcome to create skeleton methods/classes, then document the process that would happen in said method and return a static value (or call next method, whatever).**

* [Controller](#controller)
* [ControllerSources](#controller-sources)
* [Rules](#rules)
* [Interface](#interface)
* [Repository](#repository)
* [Service](#service)

## Controller
**Must be able to handle a wide variety of API methods**
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
**Must be able to support multiple sources at once. It needs to be as simple as possible to install a new source.**
```objc
//controllerSources.php
{
    //A generic class used to gives to the child classes diferent methods to the same return
    class generic_source
    private $SourceName;
    private $MehotdName;
    {
        function SourceExecute()
        {
        
        }
    }
    //Class to send to the generic_source class a generic method
    class send_generic_source extends generic_source
    {
      function __construct(){
        parent::__construct();
       }
    
    function SourceExecute(){
        
        $objcSource = new google_analytics_source());
        $method   = $this->MethodName();
        $result    = $objcSource->$method();
        return $result;
    }
    
    }
    //Class to implent the new Source Example: Google Analytics Source
    class google_analytics_source
    {
          $result = $this->getDataFromGoogleAnalytics();
          return $result;
          
          function getDataFromGoogleAnalytics()
          {
            //do all the magic
          }
    }
    //Script to Call google_analytics_source
    //src_google_analitics.php
    
         require_once 'send_generic_source.php';
         $newSource = new send_generic_source();
         $newSource->setSourceName('googleAnalytics');
         $newSource->setMethodName('getDataFromGoogleAnalytics');
         $newSource->SourceExecute();
    
}
```
## Rules
```objc
//CREATE RULES TO EACH METHODS 
public function RulesAdd(){}
public function RulesGet (){}
public function RulesPut(){}
public function RulesRemove(){}
```

## Interface
```objc
//ALL METHODS USED IN Services.php
Interface ServiceInterface.php
[...]
public function get_sources();
```

## Repository
```objc
//ALL METHODS USED TO CRUD DATA TO SERVICES.PHP
repository.php
[...]
public function get_sources()
{
    $result = $this->selectAllData();
   
}
```

## Service
**Must return JSON. I hate XML :-)**
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

