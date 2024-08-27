# Meal-planning-and-Grocery-list
# List to store available ingredients
available_ingredients = []
# Dictionary to store recipes and their required ingredients
recipes = {
    'Pasta': ['pasta', 'tomato sauce', 'cheese', 'olive oil'],
    'Salad': ['lettuce', 'tomato', 'cucumber', 'olive oil', 'lemon'],
    'Omelette': ['eggs', 'cheese', 'milk', 'salt', 'pepper'],
    'Grilled Cheese': ['bread', 'cheese', 'butter'],
    'Stir-fry': ['chicken', 'soy sauce', 'broccoli', 'carrot', 'bell pepper']
}
# Step 2: Function to add ingredients
def add_ingredients():
    ingredients = input("Enter the ingredients you have, separated by commas: ")
    new_ingredients = [ingredient.strip().lower() for ingredient in ingredients.split(',')]
    available_ingredients.extend(new_ingredients)
    print("\nIngredients added successfully!\n")
# Step 3: Function to display available ingredients
def display_ingredients():
    if available_ingredients:
        print("Currently available ingredients:")
        for ingredient in available_ingredients:
            print(f"- {ingredient}")
    else:
        print("No ingredients available.")
    print("\n")
# Step 4: Function to suggest recipes based on available ingredients
def suggest_recipes():
    print("Suggested Recipes based on available ingredients:")
    for recipe, ingredients in recipes.items():
        if all(item in available_ingredients for item in ingredients):
            print(f"- {recipe}")
    print("\n")
# Step 5: Function to generate a grocery list for a specific recipe
def generate_grocery_list(selected_recipe):
    if selected_recipe not in recipes:
        print("Recipe not found.")
        return
    
    required_ingredients = recipes[selected_recipe]
    missing_ingredients = [item for item in required_ingredients if item not in available_ingredients]

    if missing_ingredients:
        print(f"Grocery list for {selected_recipe}:")
        for item in missing_ingredients:
            print(f"- {item}")
    else:
        print(f"All ingredients for {selected_recipe} are available!")

    print("\n")
# Step 6: Function to create a weekly meal plan
def create_meal_plan():
    meal_plan = {}
    days = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']
    
    for day in days:
        recipe = input(f"Enter the recipe for {day}: ")
        meal_plan[day] = recipe
    
    print("\nWeekly Meal Plan:")
    for day, recipe in meal_plan.items():
        print(f"{day}: {recipe}")
    print("\n")
# Step 7: Main function to navigate the application
def main():
    while True:
        print("Welcome to the Meal Planner App")
        print("1. Add Ingredients")
        print("2. View Available Ingredients")
        print("3. Suggest Recipes")
        print("4. Generate Grocery List")
        print("5. Create Weekly Meal Plan")
        print("6. Exit")
        
        choice = input("Choose an option: ")
        
        if choice == '1':
            add_ingredients()
        elif choice == '2':
            display_ingredients()
        elif choice == '3':
            suggest_recipes()
        elif choice == '4':
            selected_recipe = input("Enter the recipe name for which you want a grocery list: ")
            generate_grocery_list(selected_recipe)
        elif choice == '5':
            create_meal_plan()
        elif choice == '6':
            print("Thank you for using the Meal Planner App!")
            break
        else:
            print("Invalid option. Please try again.\n")

if __name__ == "__main__":
    main()
