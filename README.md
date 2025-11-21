# CSE-Examination

def normalize_command(command):
    command = command.strip().lower()
    if command in ['n', 'north']:
        return 'N'
    elif command in ['s', 'south']:
        return 'S'
    elif command in ['e', 'east']:
        return 'E'
    elif command in ['w', 'west']:
        return 'W'
    elif command == 'stop':
        return 'STOP'
    else:
        return None

def move_player(position, direction):
    x, y = position
    if direction == 'N':
        y += 1
    elif direction == 'S':
        y -= 1
    elif direction == 'E':
        x += 1
    elif direction == 'W':
        x -= 1
    return (x, y)

def gps_tracker():
    position = (0, 0)
    print("Starting GPS Tracker. Type 'STOP' to end.")
    while True:
        command = input("Enter direction (N/S/E/W): ")
        normalized = normalize_command(command)
        if normalized == 'STOP':
            break
        elif normalized:
            position = move_player(position, normalized)
            print(f"Current position: {position}")
        else:
            print("Invalid input. Please enter N, S, E, W or STOP.")

    print(f"Final position: {position}")
    if position == (0, 0):
        print("You returned to the origin.")
    else:
        print("You did not return to the origin.")

# Run the tracker
gps_tracker()
