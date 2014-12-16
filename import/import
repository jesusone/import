function insertDB(){
		require("reader.imports.class.php");
        $user =& JFactory::getUser();
        $userId = $user->get( 'id' );
		$app    = JFactory::getApplication();
        $file_path =JPATH_ROOT."/images/imports/" ;
        $file_url =JUri::root()."/images/imports/" ;
		$filepost = $_POST['txt_file'];
        $fliename = $file_url.$filepost;
        if(file_exists($file_path.$filepost)){
           
            $sf = new TextFileReader($fliename);
            ini_set('max_execution_time', 3000); 
            $limit = 10;  
            $step = 0;
            $highestRow =  $sf->countLines();
            $total =  $sf->countLines();     
            //print_r($total);die();
            /* $highestRow = 340;
              $step = 5000;    */
               $f = fopen( $fliename, 'r') or die( 'Cannot open file '.$filepost);
                 
            do {
                $ordering = (int)$this->getNumordering();
               
                $reader =  $this->reader_limit($step,$highestRow,$sf,$limit,$total,$userId,$ordering,$fliename);
                $remain = $highestRow - $limit;  
                $highestRow = $remain; 
                $step =  $reader[1];
                $count =  $reader[3];       
                print_r($step."_".$highestRow."_".$count."</br>");   
             
            }
            while($highestRow >0);
            print_r("import ok");  die();
            $app->Redirect(JRoute::_('index.php?option=com_stc_mailing_tools&view=imports', true),'insert success !');
            /*$f = fopen( $fliename, 'r') or die( 'Cannot open file '.$filepost);
            $user =& JFactory::getUser();
            $userId = $user->get( 'id' );
            $i = (int)$this->getNumordering();
           
            while(!feof($f)) { 
                
              $string = fgets($f);
             
                
              $zip             =     substr($string, 0, 5);
              $rt_type         =     substr($string, 5, 1);
              $crid            =    substr($string, 6, 4);
              $box_c        =    substr($string, 10, 5);
              $rtac_c        =    substr($string, 15, 5);
              $rmfduc_c        =    substr($string, 20, 5);
              $busn_c        =    substr($string, 25, 5);
              $r_seas_c        =    substr($string, 30, 5);
              $city            =    substr($string, 35, 28);
              $st            =    substr($string, 63, 2);
              $cdsdate        =    substr($string, 65, 8);
              $county        =    substr($string, 73, 40);
              $b_seas_b        =    substr($string, 113, 5);
              $filler1        =    substr($string, 118, 32);
              $owgm            =    substr($string, 150, 1);
             
              //$price = $this->getPriceBook(1)->price;
              //$cost = (float)$rtac_c * (float)$price;
               
        
                $insert[$i] = new stdClass();
                $insert[$i]->state_code =     $st;
                $insert[$i]->city        =    $city;
                $insert[$i]->county        =    $county;
                $insert[$i]->zip        =    $zip;
                $insert[$i]->cr            =    $crid;
                //$insert[$i]->cost        =    $cost;
                $insert[$i]->homes        =  $rtac_c;
                $insert[$i]->created_by =  $userId;
                $insert[$i]->ordering   =  $i;
                $insert[$i]->state        =    1;
                $insert[$i]->check_date = date('Y-m-d' , strtotime ($cdsdate));
                 

                $result = JFactory::getDbo()->insertObject('#__stc_mailing_tool_routes', $insert[$i]);
                
                $i++;
            
            }
            fclose($f);   */
           //  $app->Redirect(JRoute::_('index.php?option=com_stc_mailing_tools&view=imports', true),'insert success !');
            
         
        }
        else {
             $app->Redirect(JRoute::_('index.php?option=com_stc_mailing_tools&view=imports', true),'Not exist file.');  
        }  
        
      
	} 
