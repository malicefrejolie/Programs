# Programs
Código Raspberry protótipo de automação residencial

<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
	<meta name="viewport" content = "height = device-height, width = 420, user-scalable = no" /> 
	<title>Automacao</title>
	<script type="text/javascript" src="/webiopi.js"></script>
	<script type="text/javascript">
	
 webiopi().ready(function() {
		webiopi().setFunction(23,"out");
		webiopi().setFunction(4,"out");
		webiopi().setFunction(22,"out");
		webiopi().setFunction(21,"out");
		
		var content, button;
		content = $("#content");
		
		button = webiopi().createGPIOButton(4, "SALA");
		content.append(button); 
		
		button = webiopi().createGPIOButton(23, "QUARTO");
		content.append(button); 
		
		button = webiopi().createGPIOButton(22, "CONZINHA");
		content.append(button);

		button = webiopi().createGPIOButton(21, "JARDIM");
		content.append(button);
	
		button = webiopi().createButton("l", "ABRIR", outputSequence);
		content.append(button);
		
		button = webiopi().createButton("d", "FECHAR", outputSequence1);
		content.append(button);
		      
		
	});
	
		function outputSequence() {
		webiopi().setFunction(23, "in");
		var sequence = "10"
		webiopi().outputSequence(21, 10000, sequence, liberarPorta);
		}

		function outputSequence1() {
		webiopi().setFunction(21, "in");
		var sequence = "10"
		webiopi().outputSequence(23, 10000, sequence, liberarPorta1);
		}

		function liberarPorta() {
		webiopi().setFunction(23,"out");
		webiopi().setFunction(21,"out");
		
		}

		function liberarPorta1() {
		webiopi().setFunction(23,"out");
		webiopi().setFunction(21,"out");
		
		}

	</script>
	<style type="text/css">

		button {
			display: block;
			margin: 5px 5px 5px 5px;
			width: 160px;
			height: 45px;
			font-size: 24pt;
			font-weight: bold;
			color: blue;
			
		}
		
		input[type="range"] {
			display: block;
			width: 160px;
			height: 45px;
		}
		
		#gpio23.LOW {
			background-color: White;
			
		}
		
		#gpio23.HIGH {
			background-color: Red;
			
		}
		
		#gpio4.LOW {
			background-color: White;
			
		}
		
		#gpio4.HIGH {
			background-color: Red;
			
		}
		#gpio22.LOW {
			background-color: White;
			
		}
		
		#gpio22.HIGH {
			background-color: Red;
			
		}
		#gpio21.LOW {
			background-color: White;
			
		}
		
		#gpio21.HIGH {
			background-color: Red;
			
		}
		

</style>
</head>
<body>
	<center><font color="black"><h1>Botoes da casa</h1></font></center><br><br>
	<div id="content" align="center"></div>
</body>
</html>
