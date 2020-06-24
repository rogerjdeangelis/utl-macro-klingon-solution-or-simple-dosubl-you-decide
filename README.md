# utl-macro-klingon-solution-or-simple-dosubl-you-decide
Macro klingon solution or simple dosubl you decide 
    Macro klingon solution or simple dosubl you decide                                                                               
                                                                                                                                     
    Problem sort the macro variable                                                                                                  
                                                                                                                                     
       %let STR = 15, 30, 16, 8, 86, 98, 6, 6, 100, -9;                                                                              
                                                                                                                                     
            STR = -9,6,6,8,15,16,30,86,98,100                                                                                        
                                                                                                                                     
      Two Solutions                                                                                                                  
                                                                                                                                     
            a. dosubl                                                                                                                
            b. kingon                                                                                                                
                                                                                                                                     
    You need this macro                                                                                                              
                                                                                                                                     
    %macro dosubl(arg);                                                                                                              
      %let rc=%qsysfunc(dosubl(&arg));                                                                                               
    %mend dosubl;                                                                                                                    
                                                                                                                                     
    github                                                                                                                           
    https://tinyurl.com/yajolzqa                                                                                                     
    https://github.com/rogerjdeangelis/utl-macro-klingon-solution-or-simple-dosubl-you-decide                                        
                                                                                                                                     
    StackOverflow                                                                                                                    
    https://tinyurl.com/y7wd382v                                                                                                     
    https://stackoverflow.com/questions/62501179/sas-macro-how-to-sort-a-sequence-of-separated-numbers-using-sas-macro-witho         
                                                                                                                                     
    Tom                                                                                                                              
    https://stackoverflow.com/users/4965549/tom                                                                                      
                                                                                                                                     
                                                                                                                                     
    /*             _                 _     _                                                                                         
      __ _      __| | ___  ___ _   _| |__ | |                                                                                        
     / _` |    / _` |/ _ \/ __| | | | '_ \| |                                                                                        
    | (_| |_  | (_| | (_) \__ \ |_| | |_) | |                                                                                        
     \__,_(_)  \__,_|\___/|___/\__,_|_.__/|_|                                                                                        
                                                                                                                                     
    */                                                                                                                               
                                                                                                                                     
    %symdel str list / nowarn;                                                                                                       
                                                                                                                                     
    %let str = 15, 30, 16, 8, 86, 98, 6, 6, 100, -9;                                                                                 
                                                                                                                                     
    %dosubl(%nrstr(                                                                                                                  
       data _null_;                                                                                                                  
         array x [10] _temporary_  (&str);                                                                                           
         call sortn(of x[*]);                                                                                                        
         call symputx('str',catx(',',of x[*]));                                                                                      
       run;quit;                                                                                                                     
    ));                                                                                                                              
                                                                                                                                     
    %put &=str;                                                                                                                      
                                                                                                                                     
    STR=-9,6,6,8,15,16,30,86,98,100                                                                                                  
                                                                                                                                     
    *_    _ _                                                                                                                        
    | | _| (_)_ __   __ _  ___  _ __                                                                                                 
    | |/ / | | '_ \ / _` |/ _ \| '_ \                                                                                                
    |   <| | | | | | (_| | (_) | | | |                                                                                               
    |_|\_\_|_|_| |_|\__, |\___/|_| |_|                                                                                               
                    |___/                                                                                                            
    ;                                                                                                                                
                                                                                                                                     
     options mprint symbolgen;                                                                                                       
     %let str = 15, 30, 16, 8, 86, 98, 6, 6, 100, -9;                                                                                
     %let new_list = ;                                                                                                               
                                                                                                                                     
     %macro sort(list=);                                                                                                             
         %let nWords = %sysfunc(countw(&list.));                                                                                     
         %global new_list;                                                                                                           
         %let new_list = %sysfunc(smallest(1, %unquote(&list)));                                                                     
                                                                                                                                     
         %do i=2 %to &nwords;                                                                                                        
             %let element = %sysfunc(smallest(&i, %unquote(&list)));                                                                 
             %let new_list = &new_list, &element;                                                                                    
         %end;                                                                                                                       
                                                                                                                                     
     %mend;                                                                                                                          
                                                                                                                                     
     %sort(list=%quote(&str));                                                                                                       
                                                                                                                                     
     %put &=new_list;                                                                                                                
                                                                                                                                     
     NEW_LIST=-9, 6, 6, 8, 15, 16, 30, 86, 98, 100                                                                                   
                                                                                                                                     
