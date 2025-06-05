# DetalhaUsuario.php
Consulta detalhada de usuarios.

<?php
include('segurancadez.php');
include('cabecalho.php');
include('conn.php');
if(!isset($_GET['id'])){
    header('Location: listausuarios.php');
    exit();
}
$id = $_GET['id'];
$sql = "SELECT * FROM tb_usuarios WHERE id_usuario = $id";
$result = mysqli_query($link,$sql);
$tbl = mysqli_fetch_array($result);
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
    <h1>Detalha Usuario</h1>
    <br>
    <form action="cadastracliente.php" method="post">
        <label for="nome">Nome:</label>
        <input type="text" value="<?=$tbl[1]?>" disabled>
        <br>
        <label for="apelido">Alias</label>
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
        <select id="nivel" name="nivel" disabled>
            <option value="1"<?=$tbl[16]==1?"selected":"" ?>>Usuario</option>
            <option value="10"<?=$tbl[16]==10?"selected":"" ?>>Administrador</option>
        </select>
        <br>
        <br>
        <a href="listausuarios.php"><input type="button" value="voltar">
        </a>
    </form>
</body>
</html>
