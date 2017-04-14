##How to compare five date parameters quickly? 

if the form send five date parameters to backend want to insert to database. 

How can I check it quickly? To compare each one?? 

####*User write Five date parameters:E,A,C,B,D. But date sort rule is A < B < C < D < E 

* Brute Force:

```php
  private function compareDate($A,$B,$C,$D,$E)
  {
   if($A>$B || $A>$C || $A>$D || $A>$E){
    return false;
    }
    if($B<$A || $B>$C || $B>$D || $B>$E){
    return false;
    }
  
    ..........and so on
  
   return $result;
  }
```

* Compare quickly:

```php
  private function compareDate($A,$B,$C,$D,$E)
  {
    $result=true;
    $sortArr=array($A,$B,$C,$D,$E);
  
    for($i=0;$i<count($sortArr);$i++){
        for($j=$i+1;$j<count($sortArr);$j++){
        if(strotime($sortArr[$i]) > strotime($sortArr[$j])){
         $result=false;
         break;
         }
        }
    }
   return $result;
  }
```