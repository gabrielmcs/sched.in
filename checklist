<!--**
 * @Autor: Gabriel Soares -  gabriel@sched.in
 * @Checklist para maquinas de chão de fabrica.
 *-->
<?php
//Abre session
session_start();

//Conexao com Banco de Dados
include_once("conexao.php");

//Verificar se está sendo passado na URL a página atual, senao é atribuido a pagina 
$pagina = (isset($_GET['pagina']))? $_GET['pagina'] : 1;

//Selecionar todos os passos da tabela
$result_checklist = "SELECT * FROM cadChecklist";
$resultado_checklist = mysqli_query($conn, $result_checklist);
?>

<!DOCTYPE html>
<html>
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
  <title>Checklist</title>
  <link rel="stylesheet" href="css.css" type="text/css">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css" type="text/css">
  <link rel="stylesheet" href="https://static.pingendo.com/bootstrap/bootstrap-4.3.1.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js"></script>
  <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js"></script>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css" type="text/css">
  <link rel="stylesheet" href="https://static.pingendo.com/bootstrap/bootstrap-4.3.1.css">
 
    <!-- LOADING -->
   <script type="text/javascript" src="pace-master/pace.min.js"></script>
   <link rel="stylesheet" href="pace-master/themes/red/pace-theme-minimal.css">
 <!-- LOADING -->

</head>

<body>
  <!------------------------------------------------------------------------------------- CABECALHO --------------------------------------------------------->
  <nav class="navbar fixed-top navbar-expand-md navbar-dark bg-dark" style="">
    <div class="container">
      <a class="navbar-brand" href="index.php">
        <i class="fa d-inline fa-grav fa-lg" aria-hidden="true"></i>
        <b class="">CHECKLIST</b>
      </a> <button class="navbar-toggler navbar-toggler-right border-0" type="button" data-toggle="collapse" data-target="#navbar10"><span class="navbar-toggler-icon"></span></button>
      <div class="collapse navbar-collapse" id="navbar10">
        <ul class="navbar-nav ml-auto">
          <li class="nav-item align-items-center"> <a class="nav-link" href="#"><i class="fa fa-user fa-fw text-success"></i>Cadastros</a> </li>
          <li class="nav-item"> <a class="nav-link" href="#"><i class="fa fa-user fa-fw text-warning"></i>Consultar</a> </li>
          <li class="nav-item"> <a class="nav-link" href="#"><i class="fa fa-user fa-fw text-danger"></i>Logout</a> </li>
        </ul>
        <!------------------------------------------------------------------------------- BOTAO CADASTRAR -------------------------------------------------------------------->
        <button type="button" class="btn navbar-btn ml-md-2 btn-outline-success" data-toggle="modal" data-target="#modalCadastrar">Novo Checklist</button>
        <!--------------------------------------------------------------------------- FIM BOTAO CADASTRAR -------------------------------------------------------------------->
      </div>
    </div>
  </nav>
  <!-------------------------------------------------------------------------------------- FIM DO CABECALHO --------------------------------------------------------->
  <div class="container">
    <div class="row mt-5">
      <div class="col-md-12">
        <h4 class="display-4 text-center"> Checklist Expressline</h4>
      </div>
    </div>
<!----------------------------------------------------------------------------------------- ALERTAS ------------------------------------------------------------>
<?php
//Cadastrar				
if ($_SESSION['cadErro'] == "erro_cadastrar"){
?> 
<div class="alert alert-danger alert-dismissable"> 
<strong>Erro ao cadastrar os dados.</strong> 
</div>                     
<?php
unset($_SESSION['cadErro']);
}else if($_SESSION['cadErro'] == "sucesso_cadastrar") {
?> 
<div class="alert alert-dismissable alert-success"> 
<strong>Dados cadastrados com sucesso!</strong> 
</div>                     
<?php
unset($_SESSION['cadErro']);
}
?> 
<!-------------------------------------------- FIM DOS ALERTAS ------------------------------------------------------------>
<?PHP
// LAÇO  DA CONSULTA DO BANCO

while($rows_checklist = mysqli_fetch_assoc($resultado_checklist)){ 

//Contar o total de cursos
$total_checklist = mysqli_num_rows($resultado_checklist);

//echo $total_checklist;
//echo "<br>";
?>
<!------------------------------------------------------ INICIO DO FORM --------------------------------------------------------->
<form id="form" name="form" method="POST" action="cad_checklist.php">

 <div class="row border border-dark shadow-lg p-2" style="	box-shadow: 0px 0px 4px  black;">
      <div class="col-md-6">
        <div class="card m-2">
            <div class="card-header bg-light py-2"><b>Checklist <?PHP echo $rows_checklist['id']; ?></b>&nbsp;&nbsp;-&nbsp;&nbsp;<i class="fa fa-2x fa-picture-o text-danger" data-toggle="modal" data-target="#modalLinha<?PHP echo $rows_checklist['id']; ?>" data-toggle="tooltip" data-placement="top" title="Veja uma imagens exemplo" style="cursor:pointer"></i></div>
            <div class="card-body">
              <textarea disabled name="descricao<?PHP echo $rows_checklist['id']; ?>" id="descricao<?PHP echo $rows_checklist['id']; ?>" class="form-control" id="exampleFormControlTextarea1" rows="5"><?PHP echo $rows_checklist['descricao']; ?></textarea>
            </div>
          
          <div class="form-group">
          </div>
        </div>
      </div>
      <div class="col-md-3">
        <div class="card m-2">
            <div class="card-header bg-light py-2"><b>Status</b></div>
            <div class="card-body">
              <!--   <input type="radio" id="q156" name="quality[25]" value="1" checked="checked"> Normal </label> -->
              <div class="form-check" style="">
                <input class="form-check-input " type="radio" name="condicao<?PHP echo $rows_checklist['id']; ?>" id="condicao_ok<?PHP echo $rows_checklist['id']; ?>" value="ok">
                <label class="form-check-label ml-3 py-1" for="radio_condicao1"> Conforme. </label>
              </div>
              <div class="form-check pt-2">
                <input class="form-check-input " type="radio" name="condicao<?PHP echo $rows_checklist['id']; ?>" id="condicao_nok<?PHP echo $rows_checklist['id']; ?>" value="nok">
                <label class="form-check-label ml-3 py-1" for="radio_condicao2"> N&atilde;o Conforme. </label>
              </div>
              <div class="form-check pt-2">
                <input class="form-check-input " type="radio" name="condicao<?PHP echo $rows_checklist['id']; ?>" id="condicao_na<?PHP echo $rows_checklist['id']; ?>" value="na">
                <label class="form-check-label ml-3 py-1" for="radio_condicao3"> N&atilde;o se aplica. </label>
              </div>
          </div>
        </div>
      </div>
       <div class="col-md-3">
        <!--  <i class="fa fa-5x fa-camera-retro" ></i> -->
        <!-- INICIO DO PAINEL DA IMAGEM -->
        <div class="card m-2">
            <div class="card-header bg-light py-2"><b>Enviar Foto</b></div>
            <div class="card-body" align="center">
              <br>
			  <div class="image-upload">
			  <label for="file-input">
			  <i id="camera" class="fa fa-5x fa-camera-retro" style="cursor:pointer"></i>
			  </label>
			  <input id="file-input" type="file" name="file-input" accept="image/*" multiple />
			   </div>
			  
			  
			  <div id="thumb-output"></div>
              <br>
              
            </div>
          
        </div>
        <!-- FIM DO PAINEL DA IMAGEM -->
      </div>
    </div>
    <!-- -----------------------------------------------------------FIM DA PRIMEIRA LINHA------------------------------------------------------- -->
    <div class="row">
      <div class="col-md-12">
        <hr>
      </div>
    </div>
 

   
<!------------------------------------------------------------- MODAL IMAGEM LINHA 1  ----------------------------------------------------------->
<div class="modal fade" id="modalLinha<?PHP echo $rows_checklist['id']; ?>" tabindex="-1" role="dialog" aria-labelledby="myModalLabel" aria-hidden="true">
<div class="modal-dialog modal-lg" role="document">
<div class="modal-content">
<!--
<div class="modal-header bg-danger">
<h3 class="modal-title text-light text-center" id="exampleModalLabel"><b></b></h3>
<button type="button" class="close" data-dismiss="modal" aria-label="Fechar"><span class="badge badge-pill badge-dark">X</span></button>
</div>
-->
<div class="modal-body text-left">
  
  
  <div id="carouselExampleIndicators<?PHP echo $rows_checklist['id']; ?>" class="carousel slide" data-ride="carousel">
  <ol class="carousel-indicators">
    <li data-target="#carouselExampleIndicators<?PHP echo $rows_checklist['id']; ?>" data-slide-to="0" class="active"></li>
    <li data-target="#carouselExampleIndicators<?PHP echo $rows_checklist['id']; ?>" data-slide-to="1"></li>
    <li data-target="#carouselExampleIndicators<?PHP echo $rows_checklist['id']; ?>" data-slide-to="2"></li>
  </ol>
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img class="d-block w-100" src="imagens/checklist/CK1/1.jpg" alt="Imagem 01">
	<div class="carousel-caption d-none d-md-block">
    <p>Detalhe da Imagem 1</p>
  </div>
	</div>
    <div class="carousel-item">
      <img class="d-block w-100" src="imagens/checklist/CK1/2.jpg" alt="Imagem 02">
	  	<div class="carousel-caption d-none d-md-block">
    <p>Detalhe da Imagem 2</p>
  </div>
    </div>
    <div class="carousel-item">
      <img class="d-block w-100" src="imagens/checklist/CK/3.jpg" alt="Imagem 03">
	  	<div class="carousel-caption d-none d-md-block">
    <p>Detalhe da Imagem 3</p>
  </div>
    </div>
  </div>
  <a class="carousel-control-prev" href="#carouselExampleIndicators<?PHP echo $rows_checklist['id']; ?>" role="button" data-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="sr-only">Previous</span>
  </a>
  <a class="carousel-control-next" href="#carouselExampleIndicators<?PHP echo $rows_checklist['id']; ?>" role="button" data-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="sr-only">Next</span>
  </a>
</div>
 

</div>
</div>
</div>
</div>  
<!------------------------------------------------------------FIM MODAL IMAGEM LINHA 1  ----------------------------------------------------------->  
  

<?php
 //LAÇO WHILE
	}
?>
  
  
   <!-- ------------------------------------------------------BOTÃO SUBMIT -------------------------------------------------------------------->
 	    
		<div class="row  mb-5 p-3">
      <div class="col-md-12 text-right">
        <button class="btn btn-dark btn-lg" type="submit"> Salvar </button>
      </div>
    </div>
<!-- --------------------------------------------------FIM BOTÃO SUBMIT-------------------------------------------------------------------->



  
<!-- FECHA FORM -->  
</form> 
  



    </div><!-- FIM DIV CONTAINER PRINCIPAL -->
  
  
  
  <!---------------------------------------------------------- JAVASCRIPT TOOLTIP (TITLE)------------------------------------------------------>
  <script>
  
  $(function () {
  $('[data-toggle="tooltip"]').tooltip()
})
    </script>
  <!------------------------------------------------------ FIM DO JAVASCRIPT TOOLTIP (TITLE)------------------------------------------------------------------->
  
  <!-- --------------------------------------------------------------------- RODAPÉ ----------------------------------------------------------- -->
  <div class="footer">
    <div class="bg-dark py-2">
      <div class="container">
        <div class="row">
          <div class="col-md-12">
			<h5 class="text-light text-center my-2" > Checklist Expressline&reg; - Ano <?php echo date("Y"); ?></h5>
          </div>
        </div>
      </div>
    </div>
  </div>
  <!-- ----------------------------------------------------------------------- RODAPÉ ------------------------------------------------ -->
</body>
</html>
