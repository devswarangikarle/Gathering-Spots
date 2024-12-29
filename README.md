# Gathering-Spots

In a vibrant community, a resourceful organizer named "Sam" was preparing for a large event. He had x available gathering spots in a designated area. Sam received a list of n activities, each described by three numbers: m (the number of participants), u (the starting position in meters), and v (the ending position in meters).
Sam's task was to determine if he could accommodate all participants for each activity without exceeding the available gathering spots at any moment. If he could manage to host all the activities successfully, he would announce "Yes"; otherwise, he would say "No".

def can_accommodate_activities(n, x, activities):
    # Initialize a list to keep track of participants at each position
    max_position = 1000
    participants = [0] * (max_position + 1)

    # Process each activity
    for m, u, v in activities:
        participants[u] += m
        if v + 1 <= max_position:
            participants[v + 1] -= m

    # Check if participants exceed capacity at any position
    current_participants = 0
    for p in participants:
        current_participants += p
        if current_participants > x:
            return "No"

    return "Yes"

def main():
    import sys
    input = sys.stdin.read
    data = input().splitlines()

    # Read the number of activities and capacity
    n, x = map(int, data[0].split())

    # Read the activities
    activities = []
    for i in range(1, n + 1):
        m, u, v = map(int, data[i].split())
        activities.append((m, u, v))

    # Determine if all activities can be accommodated
    result = can_accommodate_activities(n, x, activities)

    # Print the result
    print(result)

if __name__ == "__main__":
    main()
