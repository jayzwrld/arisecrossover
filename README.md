import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class ItemDropButtonApp {

    public static void main(String[] args) {
        // Create an ExecutorService
        ExecutorService executorService = Executors.newSingleThreadExecutor();
        
        // Submit the task to the executor
        executorService.submit(new Runnable() {
            @Override
            public void run() {
                // Ensure that the GUI is created on the Event Dispatch Thread
                SwingUtilities.invokeLater(new Runnable() {
                    @Override
                    public void run() {
                        createAndShowGUI();
                    }
                });
            }
        });

        // Shutdown the executor after the task has been executed (optional, based on your needs)
        executorService.shutdown();
    }

    private static void createAndShowGUI() {
        // Create the frame (window)
        JFrame frame = new JFrame("Ziru G Item Drop");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(300, 200);
        
        // Create a button to simulate getting the item
        JButton dropButton = new JButton("Get Ziru G");

        // Add an ActionListener to the button
        dropButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                // Call the method to get the item when the button is pressed
                String item = getItem();
                // Show the item in a message dialog
                JOptionPane.showMessageDialog(frame, "You got the item: " + item);
            }
        });

        // Add the button to the frame's content pane
        frame.getContentPane().add(dropButton);

        // Center the window on the screen
        frame.setLocationRelativeTo(null);

        // Make the frame visible
        frame.setVisible(true);
    }

    // Method to get the item, which always gives "Ziru G"
    public static String getItem() {
        return "Ziru G"; // You always get the item
    }
}
