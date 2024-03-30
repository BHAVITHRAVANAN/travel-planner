import java.util.ArrayList;
import java.util.Scanner;

public class TravelPlanner {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // User Input
        System.out.println("Welcome to Travel Itinerary Planner!");
        System.out.print("Enter number of destinations: ");
        int numDestinations = scanner.nextInt();

        ArrayList<Destination> itinerary = new ArrayList<>();
        for (int i = 0; i < numDestinations; i++) {
            System.out.println("\nDestination " + (i + 1));
            System.out.print("City: ");
            String city = scanner.nextLine();
            scanner.nextLine(); // Consume extra newline character
            System.out.print("Arrival Date (YYYY-MM-DD): ");
            String arrivalDate = scanner.nextLine();
            System.out.print("Departure Date (YYYY-MM-DD): ");
            String departureDate = scanner.nextLine();
            System.out.print("Preferred activities (comma separated): ");
            String preferredActivities = scanner.nextLine();

            Destination destination = new Destination(city, arrivalDate, departureDate, preferredActivities);
            itinerary.add(destination);
        }

        // Budget (placeholder, replace with actual calculations)
        System.out.print("\nEnter estimated daily budget per person: ");
        double dailyBudget = scanner.nextDouble();
        int totalDays = calculateTotalDays(itinerary);
        double estimatedCost = totalDays * dailyBudget;

        // Display Itinerary
        System.out.println("\nYour Travel Itinerary:");
        for (Destination destination : itinerary) {
            destination.printDetails();
        }
        System.out.println("Estimated Total Cost: $" + estimatedCost);

        // (Optional) Call external APIs for maps and weather based on destinations and dates

        scanner.close();
    }

    private static int calculateTotalDays(ArrayList<Destination> itinerary) {
        int totalDays = 0;
        for (Destination destination : itinerary) {
            // Parse dates and calculate difference (replace with actual date handling)
            totalDays += 2; // Placeholder for arrival and departure days
        }
        return totalDays;
    }
}

class Destination {
    private String city;
    private String arrivalDate;
    private String departureDate;
    private String preferredActivities;

    public Destination(String city, String arrivalDate, String departureDate, String preferredActivities) {
        this.city = city;
        this.arrivalDate = arrivalDate;
        this.departureDate = departureDate;
        this.preferredActivities = preferredActivities;
    }

    public void printDetails() {
        System.out.println("City: " + city);
        System.out.println("Arrival Date: " + arrivalDate);
        System.out.println("Departure Date: " + departureDate);
        System.out.println("Preferred Activities: " + preferredActivities);
        System.out.println();
    }
}
