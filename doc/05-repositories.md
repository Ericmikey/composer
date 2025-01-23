<?php
use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\Exception;

require 'vendor/autoload.php'; // Ensure PHPMailer is installed via Composer

$mail = new PHPMailer(true);

try {
    // SMTP Configuration
    $mail->isSMTP();
    $mail->Host       = 'smtp.gmail.com'; // Change for your SMTP server
    $mail->SMTPAuth   = true;
    $mail->Username   = 'your-email@gmail.com'; // Your email
    $mail->Password   = 'your-email-password'; // Your email password (use App Password if needed)
    $mail->SMTPSecure = PHPMailer::ENCRYPTION_STARTTLS;
    $mail->Port       = 587; // Port for TLS

    // Email Content
    $mail->setFrom('info.auexams@muchlearning.org', 'Exam Notifications');
    $mail->addAddress('ericmikaelson2832@gmail.com'); // Recipient

    $mail->Subject = 'Your Exam has Been Marked';
    $mail->Body = "Student Name: Ridhima Malhotra\n"
                . "Exam: ACCT460_Final_A_Rev12\n\n"
                . "Your exam has been marked. The final grade for your exam is: 70%.\n\n"
                . "Feedback:\n"
                . "DO NOT REPLY TO THIS EMAIL\n"
                . "To discuss the feedback or mark for this exam, please contact the Faculty.\n\n"
                . "Faculty Science & Technology: fst_success@athabascau.ca\n"
                . "Faculty of Business: business-support@athabascau.ca\n"
                . "Faculty of Health Disciplines: cnhsgrades@athabascau.ca\n"
                . "Faculty Humanities & Social Sciences: fhss-undergraduateunit@athabascau.ca\n";

    // Send Email
    $mail->send();
    echo 'Email sent successfully!';
} catch (Exception $e) {
    echo "Error: {$mail->ErrorInfo}";
}
?>
