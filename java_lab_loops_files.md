# LAB: JAVA LOOPS AND FILES - COMPREHENSIVE

**Thời gian:** 2 tiếng  
**Điểm:** 100 điểm  
**Chủ đề:** Loops, File I/O, và Random Numbers

## MỤC TIÊU HỌC TẬP
- Mastery của increment/decrement operators (++, --)
- Sử dụng thành thạo while, do-while, for loops
- Input validation với loops
- Running totals và sentinel values
- Nested loops cho complex patterns
- Break và continue statements
- File input/output operations
- Random number generation

---

## BÀI 1: STUDENT ATTENDANCE SYSTEM (25 điểm)

Viết chương trình `StudentAttendanceSystem.java` quản lý điểm danh sinh viên:

**Requirements:**
1. **While loop** cho menu chính
2. **Input validation** với do-while loop
3. **Increment operators** cho counting
4. **File I/O** để lưu/đọc dữ liệu điểm danh
5. **Running totals** cho statistics

**Features:**
- Thêm sinh viên vào danh sách
- Điểm danh hàng ngày (Present/Absent/Late)
- Tính tỷ lệ tham dự cho từng sinh viên
- Lưu dữ liệu vào file "attendance.txt"
- Đọc dữ liệu từ file khi khởi động

**Code Structure:**
```java
import java.io.*;
import java.util.*;

public class StudentAttendanceSystem {
    private static final String ATTENDANCE_FILE = "attendance.txt";
    private static Scanner input = new Scanner(System.in);
    private static List<String> students = new ArrayList<>();
    private static Map<String, int[]> attendanceRecord = new HashMap<>();
    // [0]: Present days, [1]: Absent days, [2]: Late days
    
    public static void main(String[] args) {
        loadAttendanceData(); // File input
        
        int choice;
        do {
            displayMenu();
            choice = getValidChoice(1, 6); // Input validation with do-while
            
            switch(choice) {
                case 1: addStudent(); break;
                case 2: markAttendance(); break;
                case 3: viewAttendanceReport(); break;
                case 4: saveAttendanceData(); break;
                case 5: viewStatistics(); break;
                case 6: 
                    saveAttendanceData();
                    System.out.println("System shutting down...");
                    break;
            }
        } while(choice != 6); // While loop for main menu
    }
    
    // Input validation using do-while
    private static int getValidChoice(int min, int max) {
        int choice;
        do {
            System.out.printf("Enter choice (%d-%d): ", min, max);
            while(!input.hasNextInt()) {
                System.out.println("Invalid input! Please enter a number.");
                input.next();
                System.out.printf("Enter choice (%d-%d): ", min, max);
            }
            choice = input.nextInt();
            input.nextLine(); // consume newline
            
            if(choice < min || choice > max) {
                System.out.printf("Choice must be between %d and %d!%n", min, max);
            }
        } while(choice < min || choice > max);
        
        return choice;
    }
}
```

**Sample File Format (attendance.txt):**
```
John Doe,15,3,2
Jane Smith,18,1,1
Mike Johnson,12,5,3
Sarah Wilson,20,0,0
```

**Sample Output:**
```
=== STUDENT ATTENDANCE SYSTEM ===
Loading attendance data from file...
4 students loaded successfully.

1. Add Student
2. Mark Attendance  
3. View Attendance Report
4. Save Data
5. View Statistics
6. Exit

Enter choice (1-6): 3

=== ATTENDANCE REPORT ===
Student Name        Present  Absent  Late   Total   Attendance %
----------------------------------------------------------------
John Doe               15      3      2      20        75.0%
Jane Smith             18      1      1      20        90.0%
Mike Johnson           12      5      3      20        60.0%
Sarah Wilson           20      0      0      20       100.0%
----------------------------------------------------------------
Class Average: 81.25%
```

---

## BÀI 2: NUMBER PATTERN GENERATOR (20 điểm)

Viết chương trình `NumberPatternGenerator.java`:

**Requirements:**
1. **For loops** cho pattern generation
2. **Nested loops** cho 2D patterns
3. **Increment/decrement operators** trong loop control
4. **Break/continue** statements cho special cases
5. **File output** để save patterns

**Patterns to implement:**
```java
// Pattern 1: Right Triangle Numbers
1
2 3
4 5 6
7 8 9 10

// Pattern 2: Pyramid Numbers  
   1
  2 3
 4 5 6
7 8 9 10

// Pattern 3: Diamond Pattern
   1
  2 3
 4 5 6
  7 8
   9

// Pattern 4: Multiplication Table
   1   2   3   4   5
   2   4   6   8  10
   3   6   9  12  15
   4   8  12  16  20
   5  10  15  20  25
```

**Implementation Example:**
```java
import java.io.*;

public class NumberPatternGenerator {
    private static PrintWriter fileOutput;
    
    public static void main(String[] args) {
        try {
            fileOutput = new PrintWriter("patterns.txt");
            
            // Generate all patterns
            generateRightTriangle(5);
            generatePyramid(4);
            generateDiamond(5);
            generateMultiplicationTable(5);
            
            fileOutput.close();
            System.out.println("All patterns saved to patterns.txt");
            
        } catch(IOException e) {
            System.out.println("Error writing to file: " + e.getMessage());
        }
    }
    
    // Right Triangle using nested for loops
    private static void generateRightTriangle(int rows) {
        System.out.println("=== RIGHT TRIANGLE PATTERN ===");
        fileOutput.println("=== RIGHT TRIANGLE PATTERN ===");
        
        int number = 1;
        for(int i = 1; i <= rows; i++) { // Outer loop for rows
            for(int j = 1; j <= i; j++) { // Inner loop for columns
                System.out.printf("%2d ", number++); // Pre-increment
                fileOutput.printf("%2d ", number - 1);
            }
            System.out.println();
            fileOutput.println();
        }
        System.out.println();
        fileOutput.println();
    }
    
    // Pyramid with spaces - demonstrate continue statement
    private static void generatePyramid(int rows) {
        System.out.println("=== PYRAMID PATTERN ===");
        fileOutput.println("=== PYRAMID PATTERN ===");
        
        int number = 1;
        for(int i = 1; i <= rows; i++) {
            // Print leading spaces
            for(int space = rows - i; space > 0; space--) { // Post-decrement
                System.out.print(" ");
                fileOutput.print(" ");
            }
            
            // Print numbers
            for(int j = 1; j <= i; j++) {
                if(number > 99) { // Use break for large numbers
                    break;
                }
                System.out.printf("%2d", number++);
                fileOutput.printf("%2d", number - 1);
            }
            System.out.println();
            fileOutput.println();
        }
    }
}
```

---

## BÀI 3: SALES REPORT ANALYZER (30 điểm)

Viết chương trình `SalesReportAnalyzer.java`:

**Requirements:**
1. **File input** đọc sales data từ CSV
2. **While loop** cho data processing
3. **Running totals** cho sales calculations
4. **Sentinel values** cho data validation
5. **Random class** để generate sample data nếu file không tồn tại

**File Format (sales_data.csv):**
```
Date,Salesperson,Product,Quantity,UnitPrice
2024-01-01,John Smith,Laptop,2,25000000
2024-01-01,Jane Doe,Mouse,5,500000
2024-01-02,Mike Johnson,Keyboard,3,800000
SENTINEL,-1,-1,-1,-1
```

**Implementation:**
```java
import java.io.*;
import java.util.*;
import java.util.Random;

public class SalesReportAnalyzer {
    private static final String SALES_FILE = "sales_data.csv";
    private static final String REPORT_FILE = "sales_report.txt";
    private static Random random = new Random();
    
    // Running totals
    private static double totalSales = 0.0;
    private static int totalTransactions = 0;
    private static Map<String, Double> salesPersonTotals = new HashMap<>();
    private static Map<String, Integer> productCounts = new HashMap<>();
    
    public static void main(String[] args) {
        // Check if sales file exists, generate if not
        File salesFile = new File(SALES_FILE);
        if(!salesFile.exists()) {
            System.out.println("Sales file not found. Generating sample data...");
            generateSampleSalesData();
        }
        
        // Process sales data
        processSalesData();
        
        // Generate comprehensive report
        generateSalesReport();
        
        System.out.println("Sales analysis complete. Check " + REPORT_FILE);
    }
    
    // Generate random sales data if file doesn't exist
    private static void generateSampleSalesData() {
        String[] salespeople = {"John Smith", "Jane Doe", "Mike Johnson", "Sarah Wilson"};
        String[] products = {"Laptop", "Mouse", "Keyboard", "Monitor", "Printer"};
        double[] prices = {25000000, 500000, 800000, 15000000, 3000000};
        
        try(PrintWriter writer = new PrintWriter(SALES_FILE)) {
            writer.println("Date,Salesperson,Product,Quantity,UnitPrice");
            
            // Generate 50 random sales records
            for(int i = 0; i < 50; i++) {
                String date = String.format("2024-01-%02d", random.nextInt(30) + 1);
                String salesperson = salespeople[random.nextInt(salespeople.length)];
                int productIndex = random.nextInt(products.length);
                String product = products[productIndex];
                int quantity = random.nextInt(10) + 1; // 1-10 quantity
                double unitPrice = prices[productIndex];
                
                writer.printf("%s,%s,%s,%d,%.0f%n", 
                             date, salesperson, product, quantity, unitPrice);
            }
            
            // Add sentinel value
            writer.println("SENTINEL,-1,-1,-1,-1");
            System.out.println("Sample data generated successfully!");
            
        } catch(IOException e) {
            System.out.println("Error generating sample data: " + e.getMessage());
        }
    }
    
    // Process sales data using while loop and sentinel values
    private static void processSalesData() {
        try(Scanner fileScanner = new Scanner(new File(SALES_FILE))) {
            // Skip header line
            if(fileScanner.hasNextLine()) {
                fileScanner.nextLine();
            }
            
            System.out.println("Processing sales data...");
            
            while(fileScanner.hasNextLine()) {
                String line = fileScanner.nextLine().trim();
                
                // Check for sentinel value
                if(line.startsWith("SENTINEL")) {
                    System.out.println("Sentinel value found. Processing complete.");
                    break;
                }
                
                // Skip empty lines
                if(line.isEmpty()) {
                    continue;
                }
                
                // Parse CSV line
                String[] fields = line.split(",");
                if(fields.length < 5) {
                    System.out.println("Invalid data format: " + line);
                    continue; // Skip invalid lines
                }
                
                try {
                    String date = fields[0];
                    String salesperson = fields[1];
                    String product = fields[2];
                    int quantity = Integer.parseInt(fields[3]);
                    double unitPrice = Double.parseDouble(fields[4]);
                    
                    // Validate data
                    if(quantity <= 0 || unitPrice <= 0) {
                        System.out.println("Invalid quantity or price: " + line);
                        continue;
                    }
                    
                    // Calculate line total
                    double lineTotal = quantity * unitPrice;
                    
                    // Update running totals
                    totalSales += lineTotal;
                    totalTransactions++;
                    
                    // Update salesperson totals
                    salesPersonTotals.put(salesperson, 
                        salesPersonTotals.getOrDefault(salesperson, 0.0) + lineTotal);
                    
                    // Update product counts
                    productCounts.put(product,
                        productCounts.getOrDefault(product, 0) + quantity);
                    
                } catch(NumberFormatException e) {
                    System.out.println("Error parsing numbers in line: " + line);
                    continue;
                }
            }
            
        } catch(FileNotFoundException e) {
            System.out.println("Sales file not found: " + e.getMessage());
        }
    }
    
    // Generate comprehensive sales report
    private static void generateSalesReport() {
        try(PrintWriter reportWriter = new PrintWriter(REPORT_FILE)) {
            
            // Report header
            reportWriter.println("=".repeat(60));
            reportWriter.println("           COMPREHENSIVE SALES REPORT");
            reportWriter.println("=".repeat(60));
            reportWriter.printf("Generated: %s%n%n", new Date());
            
            // Summary statistics
            reportWriter.println("SUMMARY STATISTICS:");
            reportWriter.printf("Total Sales Amount: ₫%,.0f%n", totalSales);
            reportWriter.printf("Total Transactions: %,d%n", totalTransactions);
            reportWriter.printf("Average Transaction: ₫%,.0f%n", 
                              totalTransactions > 0 ? totalSales / totalTransactions : 0);
            reportWriter.println();
            
            // Top performing salesperson
            reportWriter.println("SALESPERSON PERFORMANCE:");
            reportWriter.println("-".repeat(50));
            
            // Sort salespeople by total sales (descending)
            salesPersonTotals.entrySet().stream()
                .sorted(Map.Entry.<String, Double>comparingByValue().reversed())
                .forEach(entry -> {
                    String name = entry.getKey();
                    double sales = entry.getValue();
                    double percentage = (sales / totalSales) * 100;
                    reportWriter.printf("%-20s ₫%12,.0f (%5.1f%%)%n", 
                                       name, sales, percentage);
                });
            
            reportWriter.println();
            
            // Product analysis
            reportWriter.println("PRODUCT ANALYSIS:");
            reportWriter.println("-".repeat(50));
            
            productCounts.entrySet().stream()
                .sorted(Map.Entry.<String, Integer>comparingByValue().reversed())
                .forEach(entry -> {
                    reportWriter.printf("%-20s %8d units%n", 
                                       entry.getKey(), entry.getValue());
                });
            
            reportWriter.println();
            reportWriter.println("=".repeat(60));
            
            // Also display summary to console
            System.out.println("\n=== SALES ANALYSIS SUMMARY ===");
            System.out.printf("Total Sales: ₫%,.0f%n", totalSales);
            System.out.printf("Transactions: %,d%n", totalTransactions);
            System.out.printf("Average: ₫%,.0f%n", 
                            totalTransactions > 0 ? totalSales / totalTransactions : 0);
            
        } catch(IOException e) {
            System.out.println("Error writing report: " + e.getMessage());
        }
    }
}
```

---

## BÀI 4: RANDOM GAME COLLECTION (25 điểm)

Viết chương trình `RandomGameCollection.java`:

**Requirements:**
1. **Random class** cho game mechanics
2. **Do-while loops** cho game continuation
3. **For loops** cho game rounds
4. **Break/continue** cho game flow control
5. **File I/O** cho high scores

**Games included:**
- Number Guessing Game (1-100)
- Dice Rolling Simulator
- Random Password Generator
- Lottery Number Generator

```java
import java.io.*;
import java.util.*;

public class RandomGameCollection {
    private static Scanner input = new Scanner(System.in);
    private static Random random = new Random();
    private static final String SCORES_FILE = "high_scores.txt";
    
    public static void main(String[] args) {
        loadHighScores();
        
        boolean playAgain;
        do {
            displayMainMenu();
            int choice = getValidInput(1, 5);
            
            switch(choice) {
                case 1: playNumberGuessingGame(); break;
                case 2: diceRollingSimulator(); break;
                case 3: passwordGenerator(); break;
                case 4: lotteryNumberGenerator(); break;
                case 5: 
                    saveHighScores();
                    System.out.println("Thanks for playing!");
                    return;
            }
            
            System.out.print("Play another game? (y/n): ");
            playAgain = input.nextLine().toLowerCase().startsWith("y");
            
        } while(playAgain);
        
        saveHighScores();
    }
    
    // Number Guessing Game with scoring
    private static void playNumberGuessingGame() {
        System.out.println("\n=== NUMBER GUESSING GAME ===");
        
        int targetNumber = random.nextInt(100) + 1; // 1-100
        int attempts = 0;
        int maxAttempts = 10;
        boolean won = false;
        
        System.out.printf("I'm thinking of a number between 1 and 100.%n");
        System.out.printf("You have %d attempts to guess it!%n%n", maxAttempts);
        
        do {
            attempts++;
            System.out.printf("Attempt %d/%d - Enter your guess: ", attempts, maxAttempts);
            
            int guess = getValidInput(1, 100);
            
            if(guess == targetNumber) {
                won = true;
                System.out.printf("🎉 Congratulations! You won in %d attempts!%n", attempts);
                
                // Calculate score (more attempts = lower score)
                int score = Math.max(1000 - (attempts * 100), 100);
                System.out.printf("Your score: %d points%n", score);
                
                // Save high score
                saveGameScore("Number Guessing", score);
                break;
                
            } else if(guess < targetNumber) {
                System.out.println("📈 Too low! Try higher.");
            } else {
                System.out.println("📉 Too high! Try lower.");
            }
            
            // Hint system after 5 attempts
            if(attempts == 5) {
                int hint = targetNumber % 10;
                System.out.printf("💡 Hint: The number ends with digit %d%n", hint);
            }
            
        } while(attempts < maxAttempts && !won);
        
        if(!won) {
            System.out.printf("💀 Game over! The number was %d%n", targetNumber);
        }
    }
    
    // Dice Rolling Simulator
    private static void diceRollingSimulator() {
        System.out.println("\n=== DICE ROLLING SIMULATOR ===");
        
        System.out.print("How many dice to roll? (1-10): ");
        int numDice = getValidInput(1, 10);
        
        System.out.print("How many times to roll? (1-100): ");
        int numRolls = getValidInput(1, 100);
        
        int[] totalCounts = new int[numDice * 6 + 1]; // Index 0 unused
        int grandTotal = 0;
        
        System.out.println("\nRolling results:");
        System.out.println("-".repeat(50));
        
        for(int roll = 1; roll <= numRolls; roll++) {
            System.out.printf("Roll %3d: ", roll);
            
            int rollSum = 0;
            for(int die = 1; die <= numDice; die++) {
                int value = random.nextInt(6) + 1; // 1-6
                System.out.printf("[%d]", value);
                rollSum += value;
                
                // Add space between dice
                if(die < numDice) System.out.print(" ");
            }
            
            System.out.printf(" = %2d%n", rollSum);
            totalCounts[rollSum]++;
            grandTotal += rollSum;
            
            // Pause every 10 rolls for readability
            if(roll % 10 == 0 && roll < numRolls) {
                System.out.print("Press Enter to continue...");
                input.nextLine();
            }
        }
        
        // Statistics
        System.out.println("\n=== STATISTICS ===");
        System.out.printf("Total Rolls: %d%n", numRolls);
        System.out.printf("Average: %.2f%n", (double)grandTotal / numRolls);
        System.out.printf("Total Sum: %d%n", grandTotal);
        
        System.out.println("\nSum Distribution:");
        for(int sum = numDice; sum <= numDice * 6; sum++) {
            if(totalCounts[sum] > 0) {
                double percentage = (double)totalCounts[sum] / numRolls * 100;
                System.out.printf("Sum %2d: %3d times (%.1f%%) ", 
                                sum, totalCounts[sum], percentage);
                
                // Visual bar
                int barLength = (int)(percentage / 2); // Scale down for display
                for(int i = 0; i < barLength; i++) {
                    System.out.print("█");
                }
                System.out.println();
            }
        }
    }
    
    // Random Password Generator
    private static void passwordGenerator() {
        System.out.println("\n=== RANDOM PASSWORD GENERATOR ===");
        
        System.out.print("Password length (8-50): ");
        int length = getValidInput(8, 50);
        
        System.out.print("Include uppercase letters? (y/n): ");
        boolean includeUpper = input.nextLine().toLowerCase().startsWith("y");
        
        System.out.print("Include numbers? (y/n): ");
        boolean includeNumbers = input.nextLine().toLowerCase().startsWith("y");
        
        System.out.print("Include special characters? (y/n): ");
        boolean includeSpecial = input.nextLine().toLowerCase().startsWith("y");
        
        System.out.print("How many passwords to generate? (1-20): ");
        int count = getValidInput(1, 20);
        
        // Character sets
        String lowercase = "abcdefghijklmnopqrstuvwxyz";
        String uppercase = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        String numbers = "0123456789";
        String special = "!@#$%^&*()_+-=[]{}|;:,.<>?";
        
        StringBuilder charSet = new StringBuilder(lowercase);
        if(includeUpper) charSet.append(uppercase);
        if(includeNumbers) charSet.append(numbers);
        if(includeSpecial) charSet.append(special);
        
        System.out.println("\nGenerated Passwords:");
        System.out.println("-".repeat(60));
        
        for(int i = 1; i <= count; i++) {
            StringBuilder password = new StringBuilder();
            
            for(int j = 0; j < length; j++) {
                int randomIndex = random.nextInt(charSet.length());
                password.append(charSet.charAt(randomIndex));
            }
            
            System.out.printf("%2d. %s%n", i, password.toString());
        }
        
        // Save passwords to file
        try(PrintWriter writer = new PrintWriter("generated_passwords.txt", "UTF-8")) {
            writer.println("Generated Passwords - " + new Date());
            writer.println("Length: " + length + " characters");
            writer.println("Character set options:");
            writer.println("- Lowercase: yes");
            writer.println("- Uppercase: " + (includeUpper ? "yes" : "no"));
            writer.println("- Numbers: " + (includeNumbers ? "yes" : "no"));
            writer.println("- Special chars: " + (includeSpecial ? "yes" : "no"));
            writer.println("-".repeat(60));
            
            // Regenerate passwords for file (security practice)
            for(int i = 1; i <= count; i++) {
                StringBuilder password = new StringBuilder();
                for(int j = 0; j < length; j++) {
                    int randomIndex = random.nextInt(charSet.length());
                    password.append(charSet.charAt(randomIndex));
                }
                writer.printf("%2d. %s%n", i, password.toString());
            }
            
            System.out.println("\nPasswords also saved to 'generated_passwords.txt'");
            
        } catch(IOException e) {
            System.out.println("Error saving passwords to file: " + e.getMessage());
        }
    }
    
    // Utility method for input validation
    private static int getValidInput(int min, int max) {
        int value;
        do {
            while(!input.hasNextInt()) {
                System.out.printf("Please enter a number between %d and %d: ", min, max);
                input.next();
            }
            value = input.nextInt();
            input.nextLine(); // consume newline
            
            if(value < min || value > max) {
                System.out.printf("Number must be between %d and %d: ", min, max);
            }
        } while(value < min || value > max);
        
        return value;
    }
}
```

---

## ADVANCED TECHNIQUES DEMONSTRATION

### 1. Loop Selection Guidelines
```java
// Use FOR when you know exact iterations
for(int i = 0; i < 10; i++) { /* exactly 10 times */ }

// Use WHILE when condition-based looping
while(hasMoreData) { /* until data exhausted */ }

// Use DO-WHILE when you need at least one execution
do {
    userChoice = getMenuChoice();
} while(userChoice != EXIT);
```

### 2. Increment/Decrement Patterns
```java
// Pre vs Post increment
int a = 5;
int b = ++a; // a=6, b=6 (increment first)
int c = a++; // a=7, c=6 (use first, then increment)

// Loop optimization
for(int i = 0; i < array.length; ++i) { // Pre-increment slightly faster
    // Process array[i]
}
```

### 3. File I/O Best Practices
```java
// Try-with-resources for automatic closing
try(Scanner fileReader = new Scanner(new File("data.txt"));
    PrintWriter fileWriter = new PrintWriter("output.txt")) {
    
    // File operations here
    // Files automatically closed even if exception occurs
    
} catch(IOException e) {
    System.out.println("File error: " + e.getMessage());
}
```

---

## TIÊU CHÍ CHẤM ĐIỂM

| Bài tập | Điểm | Chi tiết |
|---------|------|----------|
| **Bài 1: Student Attendance System** | **25** | |
| - While loop cho menu | 5 | Main program loop |
| - Input validation với do-while | 6 | Robust user input |
| - File I/O operations | 8 | Save/load attendance data |
| - Running totals và statistics | 6 | Attendance calculations |
| **Bài 2: Number Pattern Generator** | **20** | |
| - Nested loops cho patterns | 8 | 2D pattern generation |
| - Increment/decrement usage | 4 | Proper operator usage |
| - Break/continue statements | 4 | Flow control |
| - File output formatting | 4 | Pattern file generation |
| **Bài 3: Sales Report Analyzer** | **30** | |
| - File input processing | 8 | CSV reading và parsing |
| - Sentinel values handling | 6 | Data validation |
| - Running totals calculations | 8 | Sales statistics |
| - Random data generation | 8 | Sample data creation |
| **Bài 4: Random Game Collection** | **25** | |
| - Random class usage | 8 | Game mechanics |
| - Loop combinations | 7 | Complex game flow |
| - File I/O cho scores | 5 | High score system |
| - User experience | 5 | Game polish |

---

## SUBMISSION REQUIREMENTS

**File Structure:**
```
StudentID_LoopsAndFiles/
├── src/
│   ├── StudentAttendanceSystem.java
│   ├── NumberPatternGenerator.java
│   ├── SalesReportAnalyzer.java
│   └── RandomGameCollection.java
├── data/
│   ├── attendance.txt (sample)
│   ├── sales_data.csv (sample)
│   └── high_scores.txt (sample)
├── output/
│   ├── patterns.txt
│   ├── sales_report.txt
│   └── generated_passwords.txt
└── docs/
    ├── README.md
    └── TestCases.md
```

**Documentation Requirements:**
- Explanation của mỗi loop type được sử dụng
- Justification cho loop selection decisions
- File format specifications
- Sample input/output data

**Code Quality Standards:**
- Proper exception handling
- Input validation
- Resource management (file closing)
- Meaningful variable names
- Comprehensive comments

**Deadline:** End of lab session  
**Format:** ZIP file `StudentID_LastName_LoopsAndFiles.zip`