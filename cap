<!DOCTYPE html>
<html>
<head>
    <title>Ejemplo de CAPTCHA</title>
</head>
<body>
    <form method="post" action="verificar_captcha.php">
        <label for="captcha">Ingresa el CAPTCHA:</label>
        <input type="text" id="captcha" name="captcha">
        <img src="generar_captcha.php" alt="CAPTCHA">
        <input type="submit" value="Verificar">
    </form>
</body>

<?php
session_start();

$random_string = substr(str_shuffle("ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789"), 0, 6); // Genera una cadena aleatoria de 6 caracteres
$_SESSION['captcha'] = $random_string;

$imagen = imagecreate(100, 30);
$color_fondo = imagecolorallocate($imagen, 255, 255, 255);
$color_texto = imagecolorallocate($imagen, 0, 0, 0);

imagestring($imagen, 5, 30, 8, $random_string, $color_texto);
header("Content-type: image/png");
imagepng($imagen);
imagedestroy($imagen);

session_start();

if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $usuario_captcha = $_POST['captcha'];
    
    if ($usuario_captcha === $_SESSION['captcha']) {
        echo "CAPTCHA válido. Eres humano.";
        // Aquí puedes continuar con el proceso, como enviar un formulario.
    } else {
        echo "CAPTCHA incorrecto. Inténtalo de nuevo.";
    }
} else {
    header("Location: index.html");
    exit();
}
?>

</html>


