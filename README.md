apps1
=====

error

<?php

if(!isset($_SESSION['usuario'])){
  $_SESSION['usuario'] = "av";
}

$host = "localhost";
$user = "root";
$pw = "himitsu";
$db = "tags";

$con=mysql_connect($host,$user,$pw)or die ("problemas al conectar");
mysql_select_db($db,$con)or die ("problemas al conectar la base de datos");

mysql_query("SELECT * FROM tags WHERE usuario = '".$_SESSION['usuario']."' ORDER BY hits DESC;",$con);
$resultado = mysql_query($con);
while($fila=mysql_fetch_array($resultado)){
	
echo '
	<a href="">
		<div class="boton">
			<img src="'.$fila['url'].'/favicon.ico" alt="'.$fila['url'].'" width=32px height=32px>
		</div>
	</a>
';	
}

?>
