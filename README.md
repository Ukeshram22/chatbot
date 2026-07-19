// Source code is decompiled from a .class file using FernFlower decompiler (from Intellij IDEA).
import java.awt.BorderLayout;
import java.awt.Color;
import java.awt.Component;
import java.awt.Font;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.time.LocalDate;
import java.time.LocalTime;
import java.util.Objects;
import javax.swing.BorderFactory;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JScrollPane;
import javax.swing.JTextArea;
import javax.swing.JTextField;
import javax.swing.SwingUtilities;

public class ChatBot extends JFrame implements ActionListener {
   private JTextArea chatArea;
   private JTextField inputField;
   private JButton sendButton;
   private JButton clearButton;

   public ChatBot() {
      this.setTitle("Java AI ChatBot");
      this.setSize(700, 550);
      this.setLocationRelativeTo((Component)null);
      this.setDefaultCloseOperation(3);
      this.chatArea = new JTextArea();
      this.chatArea.setEditable(false);
      this.chatArea.setFont(new Font("SansSerif", 0, 16));
      this.chatArea.setBackground(new Color(245, 245, 245));
      this.chatArea.setLineWrap(true);
      this.chatArea.setWrapStyleWord(true);
      JScrollPane var1 = new JScrollPane(this.chatArea);
      this.inputField = new JTextField();
      this.inputField.setFont(new Font("SansSerif", 0, 16));
      this.sendButton = new JButton("Send");
      this.clearButton = new JButton("Clear");
      this.sendButton.addActionListener(this);
      this.clearButton.addActionListener(new ActionListener() {
         {
            Objects.requireNonNull(ChatBot.this);
         }

         public void actionPerformed(ActionEvent var1) {
            ChatBot.this.chatArea.setText("");
            ChatBot.this.welcomeMessage();
         }
      });
      this.inputField.addActionListener(this);
      JPanel var2 = new JPanel(new BorderLayout(10, 10));
      var2.setBorder(BorderFactory.createEmptyBorder(10, 10, 10, 10));
      JPanel var3 = new JPanel();
      var3.add(this.sendButton);
      var3.add(this.clearButton);
      var2.add(this.inputField, "Center");
      var2.add(var3, "East");
      this.add(var1, "Center");
      this.add(var2, "South");
      this.welcomeMessage();
      this.setVisible(true);
   }

   private void welcomeMessage() {
      this.chatArea.append("\ud83e\udd16 ChatBot: Hello! Welcome.\n");
      this.chatArea.append("\ud83e\udd16 Ask me about Java, AI, CGPA, Time, Date or type Bye.\n\n");
   }

   public void actionPerformed(ActionEvent var1) {
      String var2 = this.inputField.getText().trim();
      if (!var2.isEmpty()) {
         this.chatArea.append("\ud83d\udc64 You : " + var2 + "\n");
         String var3 = this.getResponse(var2);
         this.chatArea.append("\ud83e\udd16 Bot : " + var3 + "\n\n");
         this.inputField.setText("");
      }
   }

   private String getResponse(String var1) {
      var1 = var1.toLowerCase();
      if (!var1.contains("hello") && !var1.contains("hi")) {
         if (var1.contains("how are you")) {
            return "I'm fine. Thanks for asking.";
         } else if (var1.contains("your name")) {
            return "My name is Java AI ChatBot.";
         } else if (var1.contains("java")) {
            return "Java is an Object-Oriented Programming Language.";
         } else if (var1.contains("ai")) {
            return "Artificial Intelligence enables computers to perform intelligent tasks.";
         } else if (var1.contains("cgpa")) {
            return "CGPA means Cumulative Grade Point Average.";
         } else if (var1.contains("project")) {
            return "Java ChatBot is a good mini project for college.";
         } else if (var1.contains("time")) {
            LocalTime var10000 = LocalTime.now();
            return "Current Time : " + String.valueOf(var10000.withNano(0));
         } else if (var1.contains("date")) {
            return "Today's Date : " + String.valueOf(LocalDate.now());
         } else if (var1.contains("thanks")) {
            return "You're welcome.";
         } else {
            return var1.contains("bye") ? "Goodbye! Have a wonderful day." : "Sorry, I don't understand your question.";
         }
      } else {
         return "Hello! Nice to meet you.";
      }
   }

   public static void main(String[] var0) {
      SwingUtilities.invokeLater(new Runnable() {
         public void run() {
            new ChatBot();
         }
      });
   }
}
