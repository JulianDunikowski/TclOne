using System;
using System.Collections.Generic;
using System.IO;

class ToDoApp {
    static string filePath = "tasks.txt";
    static List<string> tasks = new List<string>();

    static void Main() {
        LoadTasks();
        while (true) {
            Console.WriteLine("\n1. Add Task\n2. View Tasks\n3. Exit");
            string choice = Console.ReadLine();
            if (choice == "1") {
                Console.Write("Enter task: ");
                string task = Console.ReadLine();
                tasks.Add(task);
                SaveTasks();
            } else if (choice == "2") {
                Console.WriteLine("Tasks:");
                tasks.ForEach(Console.WriteLine);
            } else break;
        }
    }

    static void LoadTasks() {
        if (File.Exists(filePath)) tasks = new List<string>(File.ReadAllLines(filePath));
    }

    static void SaveTasks() {
        File.WriteAllLines(filePath, tasks);
    }
}
