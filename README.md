# DetalhaUsuario.php
Consulta detalhada de usuarios.

<?php
// Inclui arquivos de segurança, cabeçalho da página e conexão com o banco de dados //
include('segurancadez.php');
include('cabecalho.php');
include('conn.php');

// Verifica se o parâmetro 'id' foi passado via GET //
if(!isset($_GET['id'])){
    // Se não houver ID, redireciona para a lista de usuários //
    header('Location: listausuarios.php');
    exit();
}

// Obtém o ID do usuário a partir da URL //
$id = $_GET['id'];

// Consulta todos os dados do usuário com o ID informado //
$sql = "SELECT * FROM tb_usuarios WHERE id_usuario = $id";
$result = mysqli_query($link, $sql);
$tbl = mysqli_fetch_array($result); // Armazena os dados do usuário em um array //

// Fecha a conexão com o banco de dados //
if(!$tbl){
    // Se não encontrar o usuário, redireciona para a lista de usuários //
    header('Location: listausuarios.php');
    exit();
}
if(!$result){
    // Se houver erro na consulta, exibe mensagem de erro //
    echo "Erro ao consultar usuário: " . mysqli_error($link);
    exit();
}
if(!$tbl){
    // Se não encontrar o usuário, redireciona para a lista de usuários //
    header('Location: listausuarios.php');
    exit();
}
// Exibe os dados do usuário na página HTML //
if(isset($_GET['msg'])){
    echo "<script>alert('".$_GET['msg']."');</script>";
}
if(isset($_GET['erro'])){
    echo "<script>alert('".$_GET['erro']."');</script>";
}
// Fecha a conexão com o banco de dados //
mysqli_close($link);
?>


<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="cadastra.css">
    <title>Cadastra Usuario</title>
</head>
<body>
    <div class="container"> < !-- Início do container --
    <h1>Detalha Usuario</h1>
    <br>
    <form>
        <label for="nome">Nome:</label> <!-- Campo para exibir o nome do usuário -->
        <input type="text" value="<?=$tbl[1]?>" disabled> <!-- O valor do campo é preenchido com o nome do usuário a partir do array $tbl -->
        <br>
        <label for="apelido">Alias:</label>
        <input type="text" value="<?=$tbl[2]?>" disabled>
        <br>
        <label for="cpf">CPF:</label>
        <input type="text" value="<?=$tbl[3]?>" disabled>
        <br>
        <label for="email">Email:</label>
        <input type="email" value="<?=$tbl[4]?>" disabled>
        <br>
        <label for="cep">CEP:</label>
        <input type="text" value="<?=$tbl[5]?>" disabled>
        <br>
        <label for="rua">Logradouro:</label>
        <input type="text" value="<?=$tbl[6]?>" disabled>
        <br>
        <label for="numero">Numero:</label>
        <input type="text" value="<?=$tbl[7]?>" disabled>
        <br>
        <label for="bairro">Bairro:</label>
        <input type="text" value="<?=$tbl[8]?>" disabled>
        <br>
        <label for="cidade">Cidade:</label>
        <input type="text" value="<?=$tbl[9]?>" disabled>
        <br>
        <label for="uf">UF:</label>
        <input type="text" value="<?=$tbl[10]?>" disabled>
        <br>
        <label for="dt_nascimento">Data de Nascimento:</label>
        <input type="date" value="<?=$tbl[11]?>" disabled>
        <br>
        <label for="telefone">Telefone:</label>
        <input type="text" value="<?=$tbl[14]?>" disabled>
        <br>
        <label for="nivel">Nivel:</label>
        <select id="nivel" name="nivel" disabled> <!-- Campo para exibir o nível do usuário -->
            <option value="1"<?=$tbl[16]==1?"selected":"" ?>>Usuario</option> <!-- O valor do campo é preenchido com o nível do usuário a partir do array $tbl -->
            <option value="10"<?=$tbl[16]==10?"selected":"" ?>>Administrador</option> 
        </select>
        <br>
        <br>
        <a href="listausuarios.php"><input type="button" value="voltar"> <!-- Botão para voltar à lista de usuários -->
        </a>
    </div>
    </form>
</body>
</html>
