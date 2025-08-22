# online-examination
The provided code implements a basic online examination system with a graphical user interface (GUI) using Java's Swing library. The system is divided into three main classes: login, OnlineTestBegin, and OnlineExam.
Overall System Flow
Login: The application starts with a simple login form. The user enters a username and password. While the code checks for a non-empty password, it does not perform any actual validation, so any entry will grant access.
Quiz Start: Upon successful "login," a new OnlineTestBegin window appears, starting the timed quiz.
Quiz Progression: The quiz presents ten multiple-choice questions sequentially. The user can select an option and then click "Save and Next" to proceed to the next question.
Special Features: The user has the option to "Save for later," which marks the current question for review and adds a review button to the GUI. This allows the user to come back to that specific question later.
Timer: A 10-minute (600 seconds) timer runs in the background. If the time runs out, the quiz ends.
Results: After all ten questions are answered or the "Result" button is clicked (which appears after the 9th question), a message box displays the final score. The application then exits.
Class Descriptions
login
This class creates the initial login window.
GUI Components:
JTextField textField1: For entering the username.
JPasswordField textField2: For entering the password.
JButton b1: The "SUBMIT" button.
Functionality:
It implements ActionListener to handle button clicks.
When the submit button is clicked, it gets the username and password from the text fields.
It checks if the password field is not empty. If it is, a message is displayed, and the function calls itself recursively, which is a potential logical error.
If the password is not empty, it creates and displays an OnlineTestBegin object, passing the username as a title.
OnlineTestBegin
This is the main class for the quiz itself.
GUI Components:
JLabel l: Displays the current question.
JLabel l1: Displays the remaining time.
JRadioButton[] jb: An array of JRadioButton objects to represent the answer options.
JButton b1: "Save and Next" button.
JButton b2: "Save for later" or "Result" button.
Dynamically created JButtons for "Review" functionality.
Quiz Logic:
Questions and Answers: The set() method contains hardcoded questions and their respective options.
Question Tracking: The current variable keeps track of the current question index (from 0 to 9).
Score Calculation: The count variable is incremented in the actionPerformed method if the check() method returns true.
actionPerformed Method:
Save and Next: Moves to the next question and increments the score if the correct option for the current question was selected.
Save for later: Marks the current question's index in an array (m[]) and adds a new "Review" button to the frame. The question is skipped, and the quiz moves to the next one.
Review: When a "Review" button is clicked, the quiz jumps back to the marked question, and the button becomes disabled.
Result: When the b2 button's text is "Result," it calculates the final score and displays it in a JOptionPane before exiting the application.
Timer: A java.util.Timer is used to create a countdown. It updates the l1 label every second. When the timer reaches zero, it displays "Time Out" and stops.
OnlineExam
This is the entry point of the application.
main method:
It creates a new instance of the login class.
It sets the size and visibility of the login window, making the application visible to the user.
A try-catch block is used to handle exceptions, though it only prints an error message using JOptionPane.
