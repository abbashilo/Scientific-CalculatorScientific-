import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class ScientificCalculator extends JFrame implements ActionListener {
    private JTextField display;
    private double num1 = 0, num2 = 0;
    private String operator = "";
    private boolean startOfNumber = true;

    public ScientificCalculator() {
        setTitle("Scientific Calculator");
        setSize(450, 600);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);
        setLayout(new BorderLayout(10, 10));

        JPanel topPanel = new JPanel(new BorderLayout(5, 5));
        topPanel.setBorder(BorderFactory.createEmptyBorder(10, 10, 5, 10));

        JLabel creditLabel = new JLabel("This tool was produced by Engineer Abbas Hilo Ali", SwingConstants.CENTER);
        creditLabel.setFont(new Font("Arial", Font.BOLD, 12));
        creditLabel.setForeground(new Color(0, 102, 204));
        topPanel.add(creditLabel, BorderLayout.NORTH);

        display = new JTextField("0");
        display.setFont(new Font("Arial", Font.BOLD, 28));
        display.setHorizontalAlignment(JTextField.RIGHT);
        display.setEditable(false);
        display.setBackground(Color.WHITE);
        display.setBorder(BorderFactory.createLineBorder(Color.GRAY, 1));
        topPanel.add(display, BorderLayout.CENTER);

        add(topPanel, BorderLayout.NORTH);

        JPanel buttonPanel = new JPanel(new GridLayout(6, 4, 8, 8));
        buttonPanel.setBorder(BorderFactory.createEmptyBorder(5, 10, 10, 10));

        String[] buttons = {
            "sin", "cos", "tan", "sqrt",
            "log", "ln", "x^y", "C",
            "7", "8", "9", "/",
            "4", "5", "6", "*",
            "1", "2", "3", "-",
            "0", ".", "=", "+"
        };

        for (String str : buttons) {
            JButton button = new JButton(str);
            button.setFont(new Font("Arial", Font.BOLD, 16));
            button.setFocusPainted(false);
            button.addActionListener(this);
            
            if (str.equals("=") || str.equals("C")) {
                button.setBackground(new Color(255, 153, 51));
                button.setForeground(Color.WHITE);
            } else if ("+-*/x^y".contains(str) || str.equals("sin") || str.equals("cos") || str.equals("tan") || str.equals("sqrt") || str.equals("log") || str.equals("ln")) {
                button.setBackground(new Color(230, 230, 230));
            } else {
                button.setBackground(Color.WHITE);
            }
            
            buttonPanel.add(button);
        }

        add(buttonPanel, BorderLayout.CENTER);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        String command = e.getActionCommand();

        if ((command.charAt(0) >= '0' && command.charAt(0) <= '9') || command.equals(".")) {
            if (startOfNumber) {
                display.setText(command);
                startOfNumber = false;
            } else {
                if (command.equals(".") && display.getText().contains(".")) {
                    return;
                }
                display.setText(display.getText() + command);
            }
        } else if (command.equals("C")) {
            display.setText("0");
            num1 = 0;
            num2 = 0;
            operator = "";
            startOfNumber = true;
        } else if (command.equals("=")) {
            if (!operator.isEmpty()) {
                num2 = Double.parseDouble(display.getText());
                calculateResult();
                operator = "";
                startOfNumber = true;
            }
        } else if (command.equals("sqrt") || command.equals("sin") || command.equals("cos") || command.equals("tan") || command.equals("log") || command.equals("ln")) {
            num1 = Double.parseDouble(display.getText());
            calculateScientific(command);
            startOfNumber = true;
        } else {
            num1 = Double.parseDouble(display.getText());
            operator = command;
            startOfNumber = true;
        }
    }

    private void calculateResult() {
        double result = 0;
        switch (operator) {
            case "+": result = num1 + num2; break;
            case "-": result = num1 - num2; break;
            case "*": result = num1 * num2; break;
            case "/": 
                if (num2 == 0) {
                    display.setText("Error: Div by 0");
                    return;
                }
                result = num1 / num2; 
                break;
            case "x^y": result = Math.pow(num1, num2); break;
        }
        display.setText(String.valueOf(result));
    }

    private void calculateScientific(String op) {
        double result = 0;
        switch (op) {
            case "sqrt":
                if (num1 < 0) {
                    display.setText("Error: Invalid Input");
                    return;
                }
                result = Math.sqrt(num1);
                break;
            case "sin": result = Math.sin(Math.toRadians(num1)); break;
            case "cos": result = Math.cos(Math.toRadians(num1)); break;
            case "tan": result = Math.tan(Math.toRadians(num1)); break;
            case "log":
                if (num1 <= 0) {
                    display.setText("Error: Invalid Input");
                    return;
                }
                result = Math.log10(num1);
                break;
            case "ln":
                if (num1 <= 0) {
                    display.setText("Error: Invalid Input");
                    return;
                }
                result = Math.log(num1);
                break;
        }
        display.setText(String.valueOf(result));
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            new ScientificCalculator().setVisible(true);
        });
    }
}
