cs297
=====

SJSU - Masters Project - Implement Syntax parameter

Testing Step
* Clone or download the zip.
* Run "node_modules\sweet.js\browser\editor.html" , to run the file you need to host the project.


Test Case:
``` JavaScript
syntaxparam it => (function(x) {
         if(x==null) {
            return "To be used in Anaphoric-If"
         }
           else {
               return x;
           }
         })

macro aif {
    case {$aif_name  
        ($cond ...) {$tru ...} else { $els ... }
     } => {
        var stxId = syntaxLocalValue(#{it})
        var it=stxId(#{$cond ...})
        replaceSyntaxParam("it",it ,#{$aif_name})
       return #
	  {
            (function () {
			
                 if ($cond ...) {
                    $tru ...
                } else {
                    $els ...
                }
            })
	
        }
    }
}

macro unless {
    case { 
	  $unless_name 
	  ($cond ...) { $body ...} } => {
 return #{
        while (true) {
		
            aif ($cond ...) {
                // `it` is correctly bound by `aif`
                console.log("loop finished at: " + it);
                            } else {
							
                $body ...
            }
        }}
    }
}


x=2
unless ((2+3)) {
    // `it` is not bound!
    console.log(it)
}
```


