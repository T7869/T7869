import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.HashMap;
import java.util.Map;

public class Register {
    private static Map<String, String> registeredUsers = new HashMap<>();
    private static QuizManager quizManager = new QuizManager();

    public static void main(String[] args) {
        JFrame frame = new JFrame("LOGIN AND REGISTRATION");
        frame.setSize(600, 500);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLayout(null);

        String[] roles = {"Admin", "Moderator", "Corporate Moderator", "Student"};
        JComboBox<String> roleComboBox = new JComboBox<>(roles);
        roleComboBox.setBounds(150, 180, 200, 30);
        frame.add(roleComboBox);

        JButton login = new JButton("Log In");
        login.setBounds(150, 220, 200, 50);
        frame.add(login);

        JButton register = new JButton("Register");
        register.setBounds(150, 290, 200, 50);
        frame.add(register);

        JLabel timerLabel = new JLabel("Time Remaining: 30 seconds");
        timerLabel.setBounds(150, 350, 200, 30);
        frame.add(timerLabel);

        // Timer implementation
        Timer timer = new Timer(1000, new ActionListener() {
            int timeLeft = 30; // 30 seconds countdown

            @Override
            public void actionPerformed(ActionEvent e) {
                if (timeLeft > 0) {
                    timeLeft--;
                    timerLabel.setText("Time Remaining: " + timeLeft + " seconds");
                } else {
                    ((Timer) e.getSource()).stop();
                    JOptionPane.showMessageDialog(frame, "Time's up! Please try again.");
                    frame.dispose(); // Close the window after timeout
                }
            }
        });

        // Start the timer when the register button is clicked
        register.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                timer.start();
                JOptionPane.showMessageDialog(frame, "Timer started! Complete registration in 30 seconds.");
            }
        });

        frame.setVisible(true);
    }
}

// Dummy QuizManager class
class QuizManager {
    // Placeholder for the real implementation
}


<!---
T7869/T7869 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
