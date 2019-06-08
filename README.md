# mail-in-java

package send_mail;

import java.util.Properties;
import javax.mail.*;
import javax.mail.internet.*;

/**
 *
 * @author Rujanth
 */
public class Send_mail {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {

        String host = "smtp.gmail.com";
        final String user = "rujanththth@gmail.com";//change accordingly  
        final String password = "****";//change accordingly  

        String to = "sajerex@gmail.com ";//change accordingly  

        //Get the session object  
        Properties props = new Properties();
        props.put("mail.smtp.host", host);
        props.put("mail.smtp.auth", "true");
        props.put("mail.smtp.port", "587");
        props.put("mail.smtp.starttls.enable",true);

        Session session = Session.getDefaultInstance(props,
                new javax.mail.Authenticator() {
            protected PasswordAuthentication getPasswordAuthentication() {
                return new PasswordAuthentication(user, password);
            }
        });

        //Compose the message  
        try {
            MimeMessage message = new MimeMessage(session);
            message.setFrom(new InternetAddress(user));
            message.addRecipient(Message.RecipientType.TO, new InternetAddress(to));
            message.setSubject("javatpoint");
           message.setContent("<!DOCTYPE html>\n" +
        "<html lang=\"en\">\n" +
        "<head>\n" +
        "    <meta charset=\"UTF-8\">\n" +
        "\n" +
        "    <title>Invoice</title>\n" +
        "\n" +
        "</head>\n" +
        "<body>\n" +
        "\n" +
        "<h2 align=\"center\">Jeff's Fishing Shack</h2>\n" +
        "<h1 align=\"center\">Tax Invoice</h1>\n" +
        "\n" +
        "Jeff's Fishing Shack\n" +
        "Trading as:Octopus Ptv Ltd\n" +
        "<BR><BR>\n" +
        "\n" +
        "Shop 4,Hillarys Boat Harbour\n" +
        "<br><BR>\n" +
        "\n" +
        "Hillarys,WA,6025\n" +
        "<br><BR>\n" +
        "\n" +
        "T:<a href=\"08 9402 2222\" >08 9402 2222</a><BR>\n" +
        "E:<a href=\" Sales@JFS.com.au\" >Sales@JFS.com.au</a>\n" +
        "<BR>\n" +
        "<p align=\"right\">Date:</p>\n" +
        "Receipt#:\n" +
        "Customer:<BR> Rujanth\n" +
        "<Br>\n" +
        "hsf2222h\n" +
        "<Br>\n" +
        "<Br>\n" +
        "Customer#: <Br>\n" +
        "Customer email:\n" +
        "<Br><Br><Br>\n" +
        "Purchases<Br><Br>\n" +
        "\n" +
        "<br>\n" +
        "<br>\n" +
        "<br>\n" +
        "<h2 align=\"right\">Total Paid:</h2>\n" +
        "<br>\n" +
        "<br>\n" +
        "\n" +
        "<p align=\"center\" style=\"font-size: 20px;\">Thank you for your business.\n" +
        "</p>\n" +
        "<p align=\"center\"style=\"font-size: 20px;\">Jeff's-Where the real fisherman shop</p>\n" +
        "</body>\n" +
        "</html>","text/html");


            //send the message  
            Transport.send(message);

            System.out.println("message sent successfully...");

        } catch (MessagingException e) {
            e.printStackTrace();
        }
    }
}
