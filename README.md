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
