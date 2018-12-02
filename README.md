# ConvNetJS-minified-library
ConvNetJS minified library, the source is from :https://cs.stanford.edu/people/karpathy/convnetjs/build/convnet-min.js

Link the minified file in the index file in your text-editor to get started instanatly:

Example code to get started:

    <html>
    <head>
      <title>Getting Started</title>
    <!--CSS goes here-->
    <style>
    body{
         background-color: red; /**Example**/
      }
     </style>
     
     <!--Importing the convetjs library-->
     <script src="minified.js">
     </script>
     
     <!--Javascript Content-->
     <script type="text/javascript">
     
    function periodic() {
    var d = document.getElementById('eg-divison');
    d.innerHTML = 'Random number: ' + Math.random()
    }
 
    var net; //global variable declared outside
    function start() {

      // this gets executed on startup
      //... 

      net = new convnetjs.Net();
      // ...

      // example of running something every 1 second
      setInterval(periodic, 1000);
    }


    </script>
    </head>

    <body onload="start()">
    <div id="eg-division"></div>
    </body>
    </html>     
    
# Neural Net Classification 
Simple two layer network binary classifier, 2 dimensional data points.
First Layer of network - input layer ,declare size of input data.
ConvNetJS layers - based on Vol, 3 dimensional(sx,sy,depth) volume of numbers.
Next three layers - fully connected ('fc').
Last layer - Classifier layer ('softmax') , outputs probability.

In case of not using images , input volume be 1x1x2
Declaring size of input volume (out_sx=1,out_sy=1,out_depth=2)

    //layer definitions
    var layer_defs=[];
    //Declaring size- 1x1x2 (vol class - 3D volume)
    layer_defs.push({type:'input', out_sx:1, out_sy:1, out_depth:2});
    //Fully Connected Layers ('fc')
    layer_defs.push({type:'fc', num_neurons:20, activation:'relu'});
    layer_defs.push({type:'fc', num_neurons:20, activation:'relu'});
    //Softmax
    layer_defs.push({type:'softmax', num_classes:2});
    
    //Creating a net 
    var net = new convnetjs.Net();
    net.makeLayers(layer_defs);
    
    //Creating a volume
    var x = new convnetjs.Vol([0.5, -1.3]);
    
    var probability_volume = net.forward(x);
    console.log('probability that x is class 0: ' + probability_volume.w[0]);
    // prints 0.50101
