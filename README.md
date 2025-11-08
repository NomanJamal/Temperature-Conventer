# Temperature-Conventer


import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class TemperatureConverterGUI {
    public static void main(String[] args) {
        // Frame 
        JFrame frame = new JFrame("Temperature Converter");
        frame.setSize(400, 300);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLayout(null);
        frame.getContentPane().setBackground(new Color(245, 245, 245));

        // Title Label
        JLabel titleLabel = new JLabel("Temperature Converter");
        titleLabel.setBounds(80, 20, 250, 30);
        titleLabel.setFont(new Font("Arial", Font.BOLD, 18));
        titleLabel.setHorizontalAlignment(SwingConstants.CENTER);
        frame.add(titleLabel);

        // Input Label
        JLabel inputLabel = new JLabel("Enter Temperature:");
        inputLabel.setBounds(50, 70, 150, 25);
        frame.add(inputLabel);

        // Input Field
        JTextField tempField = new JTextField();
        tempField.setBounds(200, 70, 120, 25);
        frame.add(tempField);

        // Combo Box for unit selection
        String[] options = {"Celsius to Fahrenheit", "Fahrenheit to Celsius"};
        JComboBox<String> unitBox = new JComboBox<>(options);
        unitBox.setBounds(100, 110, 200, 25);
        frame.add(unitBox);

        // Convert Button
        JButton convertButton = new JButton("Convert");
        convertButton.setBounds(140, 150, 120, 30);
        convertButton.setBackground(new Color(100, 149, 237));
        convertButton.setForeground(Color.WHITE);
        frame.add(convertButton);

        // Result Label
        JLabel resultLabel = new JLabel("");
        resultLabel.setBounds(50, 200, 300, 30);
        resultLabel.setHorizontalAlignment(SwingConstants.CENTER);
        resultLabel.setFont(new Font("Arial", Font.BOLD, 14));
        frame.add(resultLabel);

        // Button Action
        convertButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                try {
                    double temp = Double.parseDouble(tempField.getText());
                    String choice = (String) unitBox.getSelectedItem();
                    double convertedTemp = 0;

                    if (choice.equals("Celsius to Fahrenheit")) {
                        convertedTemp = (temp * 9 / 5) + 32;
                        resultLabel.setForeground(new Color(34, 139, 34));
                        resultLabel.setText(String.format("%.2f °C = %.2f °F", temp, convertedTemp));
                    } else {
                        convertedTemp = (temp - 32) * 5 / 9;
                        resultLabel.setForeground(new Color(255, 69, 0));
                        resultLabel.setText(String.format("%.2f °F = %.2f °C", temp, convertedTemp));
                    }
                } catch (NumberFormatException ex) {
                    resultLabel.setForeground(Color.RED);
                    resultLabel.setText("Please enter a valid number!");
                }
            }
        });

        // Frame visible
        frame.setVisible(true);
    }
}
 
