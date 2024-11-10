# trainee-strength-evaluator
def calculate_strongest_trainees(strength_values):
    # Check if all strength values are within the valid range (1 to 200)
    if any(s < 1 or s > 200 for s in strength_values):
        return "INVALID INPUT"

    # Number of trainees and rounds
    trainees = 4
    rounds = 3

    # Calculate average strength per trainee
    averages = []
    for i in range(trainees):
        # Each trainee's strength levels across rounds
        trainee_strength = strength_values[i::trainees]
        # Calculate the average strength, rounded to the nearest integer
        avg_strength = round(sum(trainee_strength) / rounds)
        averages.append(avg_strength)

    # Find the highest average strength
    max_average = max(averages)

    # If the highest average is less than 100, all trainees are unfit
    if max_average < 100:
        return "All trainees are unfit."

    # Find the strongest trainee(s)
    strongest_trainees = [i + 1 for i, avg in enumerate(averages) if avg == max_average]

    # Output the result
    result = []
    for trainee in strongest_trainees:
        result.append(f"Trainee Number : {trainee}")
    
    return "\n".join(result)


# Sample Input
strength_values = [
    150, 160, 155, 158,  # Round 1
    140, 130, 125, 142,  # Round 2
    160, 135, 125, 140   # Round 3
]

# Output the result
print(calculate_strongest_trainees(strength_values))
