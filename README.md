

<?php
require_once(__DIR__ . '/globals.php');
use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\Exception;
require_once(__DIR__ . '/../vendor/phpmailer/phpmailer/src/PHPMailer.php');
require_once(__DIR__ . '/../vendor/phpmailer/phpmailer/src/Exception.php');
require_once(__DIR__ . '/../vendor/phpmailer/phpmailer/src/SMTP.php');

$mail = new PHPMailer(true);

try {
    $mail->isSMTP();
    $mail->Host       = $GLOBALS['email_smtp_host'];
    $mail->SMTPAuth   = true;
    $mail->Username   = $GLOBALS['email_smtp_user'];
    $mail->Password   = $GLOBALS['email_smtp_pass'];
    $mail->SMTPSecure = PHPMailer::ENCRYPTION_STARTTLS;
    $mail->Port       = $GLOBALS['email_smtp_port'];
    $mail->SMTPDebug = 4; 
    $mail->SMTPOptions = [
    'socket' => [
        'bindto' => '0.0.0.0:0', // IPv4 only
    ],
];
$mail->Debugoutput = 'html';

    $mail->setFrom($GLOBALS['email_address'], 'OpenEMR Test');
    $mail->addAddress('rakeshw@cybage.com');

    $mail->Subject = 'Test Email from OpenEMR';
    $mail->Body    = 'This is a test email from OpenEMR SMTP configuration.';

    $mail->send();
    echo 'Test email sent successfully.';
} catch (Exception $e) {
    echo "Email failed: {$mail->ErrorInfo}";
}




$GLOBALS['email_enable_smtp'] = true;
$GLOBALS['email_smtp_host'] = 'smtp.gmail.com';
$GLOBALS['email_smtp_port'] = 587;
$GLOBALS['email_smtp_user'] = 'befitjournal1@gmail.com';
$GLOBALS['email_smtp_pass'] = 'pfmgwkataeqevcdc';
$GLOBALS['email_smtp_auth'] = true;
$GLOBALS['email_smtp_secure'] = 'tls';
$GLOBALS['email_address'] = 'befitjournal1@gmail.com';
$GLOBALS['email_from_name'] = 'Openemr';
