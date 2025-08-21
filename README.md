
<?php
require 'vendor/autoload.php';

use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\Exception;

$mail = new PHPMailer(true);

try {
    $mail->isSMTP();
    $mail->Host       = "smtp.gmail.com";
    $mail->SMTPAuth   = true;
    $mail->Username   = "";
    $mail->Password   ='';
    $mail->SMTPSecure = PHPMailer::ENCRYPTION_STARTTLS;
    $mail->Port       = 587;
    $mail->SMTPDebug = 4; 
    $mail->SMTPOptions = [
    'socket' => [
        'bindto' => '0.0.0.0:0', 
    ],
];
$mail->Debugoutput = 'html';

    $mail->setFrom("", 'OpenEMR Test');
    $mail->addAddress('');

    $mail->Subject = 'Test Email from OpenEMR';
    $mail->Body    = 'This is a test email from OpenEMR SMTP configuration.';

    $mail->send();
    echo 'Test email sent successfully.';
} catch (Exception $e) {
    echo "Email failed: {$mail->ErrorInfo}";
}
