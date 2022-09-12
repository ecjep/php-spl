# php-spl
Simple spl_auto_load_register


       spl_autoload_register(function($class) {

          $cs = explode("\\",$class);
          $cr = [];
          for($i=0; $i<count($cs)-1;$i++) {
          $cr[] = lcfirst($cs[$i]);
           }
          $cr[] = $cs[count($cs)-1] .".php";
          $fileName = $_SERVER['DOCUMENT_ROOT'] . '/'.implode("/",$cr);
          if (file_exists($fileName)) {
             require_once $fileName;

          }
         });
