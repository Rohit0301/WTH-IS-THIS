# WTF-is-this

// normal mode | 'use strict' mode


//console </br>
+console.log(this); 	//window | window
</br>

//IIFE</br>
(function fn(){</br>
	console.log(this); 	// window | undefined </br>
})()</br>

</br>
//function</br>
function fn1(){</br>
	console.log(this); 	//window | undefined</br>
}</br>
</br>
//timout inside funtion</br>
function fn2(){</br>
	setTimeout(()=>{</br>
		console.log(this) 	//window | undefined</br>
	},1000);</br>
}</br>
</br>
//promise inside function</br>
function fn3(){</br>
	var p = new Promise((re,ro)=>{</br>
		console.log(this); 	//window | undefined</br>
	})</br>
}</br>
</br>
//function expression</br>
var fn4 = function() {</br>
	console.log(this); 	//window | window</br>
}</br>

</br>
//arrow-function
const fn5 = () => {
	console.log(this); 	//window | undefined
}

//timout inside arrow-funtion
const fn6 = () => {
	setTimeout(()=>{
		console.log(this,"1") 	//window | window
	},1000);
}

//promise inside-function
const fn7 = () => {
	var p = new Promise((re,ro)=>{
		console.log(this,"2"); 	//window | window
	})
}

//arrow-function expression
var fn8 = () => {
	console.log(this,"7"); 	//window | window
}



//object
var obj = {
	name: "Rohit",
	surname: console.log(this),  //window | window

	//function inside object
	fn: function(){
		console.log(this); 	//Obj | Obj
		},

	//arrow-function inside object
	fn1: () => {
		console.log(this); 	//window | window
		},
	fn2: function(){

			//function inside function inside object
			function inner(){
				console.log(this); 	//window  | undefined
			} 

			//arrow-function inside function inside object
			const inner1 = () => {
				console.log(this) 	//Obj | Obj
			} 
			// inner()
			// inner1()
		},
	fn3: () => {
			//function inside arrow-function inside object
			function inner(){
				console.log(this); 	//window | undefined
			}

			//arrow-function arrow-inside function inside object
			const inner1 = () => {
				console.log(this) 	//window | window
			} 
			// inner()
			// inner1()
		}
}


setTimeout(()=>{

	//function inside timeout
	function fn(){
		console.log(this,"1"); 	//window | undefined
		
		//function inside function inside timeout
		function fn1(){
			console.log(this,"2"); //window | undefined
		}

		//arrow-function inside function inside timeout
		const fn2 = () => {
			console.log(this,"3"); //window | undefined
		}
		// fn1() 
		// fn2()
	}

	//arrow-function inside timeout
	const fn1 = () => {
		console.log(this,"4"); 	//window | window

		//function inside arrow-function inside timeout
		function fn1(){
			console.log(this,"5"); //window | undefined
		}

		//arrow-function inside arrow-function inside timeout
		const fn2 = () => {
			console.log(this,"6"); 	//window | window
		}
		// fn1() 
		// fn2()
	}
	// fn()
	// fn1()

})


// fn()
// fn1()
// fn2()
// fn3()
// fn4()
// fn5()
// fn6()
// fn7()
// fn8()


// obj.fn()
// obj.fn1()
// obj.fn2()
// obj.fn3()
`
