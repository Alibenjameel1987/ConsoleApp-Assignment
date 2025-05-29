# ConsoleApp-Assignment
using System;
using System.Collections.Generic;
using System.Text;

class Program
{
    static void Main(string[] args)
    {
        // Student name identification
        Console.WriteLine("Student: Ali Al Gasat\n");
        
        // ======== PART 1 ========
        Console.WriteLine("======== PART 1: String Array Modification ========\n");
        
        // Initialize arrays with sentence starters and endings
        string[] sentenceStarters = { "Welcome to The", "I'm Principal, ", "Our goal is to provide our students with a " };
        string[] sentenceEnders = { " Academy.", "", " Learning experience." };
        List<string> userInputs = new List<string>();

        // Collect user inputs
        Console.WriteLine("Please enter a noun:");
        userInputs.Add(Console.ReadLine());
        Console.WriteLine("Please enter the name of someone infamous:");
        userInputs.Add(Console.ReadLine());
        Console.WriteLine("Please enter an adjective:");
        userInputs.Add(Console.ReadLine());

        // Modify and display sentences
        Console.WriteLine("\nGenerated Sentences:");
        for (int i = 0; i < sentenceStarters.Length; i++)
        {
            sentenceStarters[i] += userInputs[i];
            Console.WriteLine(sentenceStarters[i] + sentenceEnders[i]);
        }
        Console.ReadLine();

        // ======== PART 2 ========
        Console.WriteLine("\n======== PART 2: Infinite Loop Fix ========\n");
        
        Console.WriteLine("Counting from 1 to 5:");
        // Fixed loop (original infinite version commented out)
        for (int i = 1; i <= 5; /* i-- would cause infinite loop */ i++)
        {
            Console.WriteLine(i);
        }
        Console.ReadLine();

        // ======== PART 3 ========
        Console.WriteLine("\n======== PART 3: Loop Comparisons ========\n");
        
        // Using '<' operator for loop comparison
        StringBuilder ghostSound = new StringBuilder();
        ghostSound.Append("B");
        while (ghostSound.Length < 10)
        {
            ghostSound.Append("o");
        }
        ghostSound.Append("!");
        Console.WriteLine(ghostSound);

        // Using '<=' operator for loop comparison
        StringBuilder surpriseSound = new StringBuilder();
        surpriseSound.Append("A");
        while (surpriseSound.Length <= 10)
        {
            surpriseSound.Append("h");
        }
        surpriseSound.Append("!");
        Console.WriteLine(surpriseSound);
        Console.ReadLine();

        // ======== PART 4 ========
        Console.WriteLine("\n======== PART 4: List Search ========\n");
        
        List<string> teams = new List<string> { 
            "Bucket", "Report", "Callice", "Meet", "Pacers", "76ers", "Mets", "Magic",
            "Wizards", "Horrors", "Bulls", "Knicks", "Pistons", "Hooks", "Cavaliers" 
        };

        Console.WriteLine("WBA Eastern Conference Standing:");
        int position = 0;
        bool validTeam = false;
        int teamIndex = 0;

        while (!validTeam)
        {
            Console.WriteLine("Enter team name:");
            string requestedTeam = Console.ReadLine();
            
            // Search for team in list
            for (int i = 0; i < teams.Count; i++)
            {
                if (teams[i].Equals(requestedTeam, StringComparison.OrdinalIgnoreCase))
                {
                    position = i + 1;
                    teamIndex = i;
                    validTeam = true;
                    break; // Exit loop once match found
                }
            }

            // Handle invalid team name
            if (!validTeam)
            {
                Console.WriteLine("That is not a valid team name. Please try again.");
            }
        }

        Console.WriteLine($"Processing... Index: {teamIndex}");
        Console.WriteLine($"Standing position: {position}");
        Console.ReadLine();

        // ======== PART 5 ========
        Console.WriteLine("\n======== PART 5: List Search with Duplicates ========\n");
        
        List<string> tableStatuses = new List<string> { 
            "Password", "Macint", "Taken", "Macint", "Macint", "Reserved", "Taken" 
        };

        Console.WriteLine("Welcome to Small Taco!\n");
        Console.WriteLine("To check in:\n- Type 'Password' if you have a reservation\n" +
                          "- Type 'Taken' if joining an existing party\n" +
                          "- Type 'Macint' for walk-in availability\n");
        
        string userSelection;
        bool validSelection = false;
        
        do
        {
            Console.WriteLine("Enter your selection:");
            userSelection = Console.ReadLine();
            
            validSelection = userSelection == "Password" || 
                             userSelection == "Taken" || 
                             userSelection == "Macint";
            
            if (!validSelection)
            {
                Console.WriteLine("Invalid choice. Please enter 'Password', 'Taken', or 'Macint'.");
            }
        } while (!validSelection);

        Console.WriteLine($"Tables matching '{userSelection}':");
        for (int i = 0; i < tableStatuses.Count; i++)
        {
            if (tableStatuses[i].Equals(userSelection, StringComparison.OrdinalIgnoreCase))
            {
                Console.WriteLine($"Table #{i + 1}");
            }
        }
        Console.ReadLine();

        // ======== PART 6 ========
        Console.WriteLine("\n======== PART 6: Duplicate Detection ========\n");
        
        List<string> studentNames = new List<string> { "Body", "Jin", "Tiffany", "Bob", "Kat", "Mary", "Mary" };
        List<string> uniqueNames = new List<string>();

        Console.WriteLine("Class Roster Analysis:");
        foreach (string name in studentNames)
        {
            if (uniqueNames.Contains(name))
            {
                Console.WriteLine($"{name} - DUPLICATE (use last initial)");
            }
            else
            {
                Console.WriteLine($"{name} - unique");
                uniqueNames.Add(name);
            }
        }
        
        Console.WriteLine("\nAssignment complete. Press Enter to exit...");
        Console.ReadLine();
    }
}
