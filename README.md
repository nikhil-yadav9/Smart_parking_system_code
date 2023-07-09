# Smart_parking_system_code
Smart parking system code in python.....
import time

# Mock sensor data for available parking spots
sensor_data = {
    'A1': True,
    'A2': True,
    'A3': False,
    'B1': True,
    'B2': False,
    'B3': True
}

# Function to check parking spot availability
def check_availability(spot_id):
    if spot_id in sensor_data:
        return sensor_data[spot_id]
    else:
        return False

# Function to reserve a parking spot
def reserve_spot(spot_id):
    if spot_id in sensor_data and sensor_data[spot_id]:
        sensor_data[spot_id] = False
        return True
    else:
        return False

# Function to free up a parking spot
def free_spot(spot_id):
    if spot_id in sensor_data and not sensor_data[spot_id]:
        sensor_data[spot_id] = True
        return True
    else:
        return False

# Main program loop
while True:
    # Print available parking spots
    print("Available parking spots:")
    for spot, availability in sensor_data.items():
        if availability:
            print(spot)
    
    
    action = input("Enter 'reserve' to reserve a spot, 'free' to free up a spot, or 'exit' to quit: ")
    
    if action == 'reserve':
        spot_id = input("Enter the spot ID to reserve: ")
        if check_availability(spot_id):
            if reserve_spot(spot_id):
                print(f"Spot {spot_id} has been reserved.")
            else:
                print(f"Unable to reserve spot {spot_id}.")
        else:
            print(f"Spot {spot_id} is not available.")
    elif action == 'free':
        spot_id = input("Enter the spot ID to free up: ")
        if free_spot(spot_id):
            print(f"Spot {spot_id} has been freed up.")
        else:
            print(f"Unable to free up spot {spot_id}.")
    elif action == 'exit':
        print("Exiting the program...")
        break
    else:
        print("Invalid action. Please try again.")

    print("--------------------------------------")
    time.sleep(1)  # Pause for 1 second before the next iteration
