# Temperature-Conventer
This is the Level 1 Task 1


import java.util.Scanner;

public class TemperatureConverter {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("=== Temperature Converter ===");
        System.out.print("Enter temperature value: ");
        double temperature = sc.nextDouble();

        System.out.print("Enter unit (C for Celsius, F for Fahrenheit): ");
        char unit = sc.next().toUpperCase().charAt(0);

        double convertedTemp;
        String convertedUnit;

        if (unit == 'C') {
            // Convert Celsius to Fahrenheit
            convertedTemp = (temperature * 9 / 5) + 32;
            convertedUnit = "Fahrenheit";
        } else if (unit == 'F') {
            // Convert Fahrenheit to Celsius
            convertedTemp = (temperature - 32) * 5 / 9;
            convertedUnit = "Celsius";
        } else {
            System.out.println("Invalid unit entered! Please enter 'C' or 'F'.");
            sc.close();
            return;
        }

        System.out.printf("Converted Temperature:", convertedTemp, convertedUnit);
        sc.close();
    }
}
