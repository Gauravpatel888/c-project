#include <iostream>
#include <string>
#include <vector>

using namespace std;

class Hotel {
private:
    vector<string> rooms;
    int totalRooms;

public:
    Hotel(int totalRooms) {
        this->totalRooms = totalRooms;
        for (int i = 0; i < totalRooms; i++) {
            rooms.push_back("Available");
        }
    }

    void bookRoom(int roomNumber) {
        if (roomNumber > 0 && roomNumber <= totalRooms) {
            if (rooms[roomNumber - 1] == "Available") {
                rooms[roomNumber - 1] = "Booked";
                cout << "Room " << roomNumber << " booked successfully!" << endl;
            } else {
                cout << "Room " << roomNumber << " is already booked." << endl;
            }
        } else {
            cout << "Invalid room number." << endl;
        }
    }

    void cancelBooking(int roomNumber) {
        if (roomNumber > 0 && roomNumber <= totalRooms) {
            if (rooms[roomNumber - 1] == "Booked") {
                rooms[roomNumber - 1] = "Available";
                cout << "Booking for room " << roomNumber << " cancelled successfully!" << endl;
            } else {
                cout << "Room " << roomNumber << " is not booked." << endl;
            }
        } else {
            cout << "Invalid room number." << endl;
        }
    }

    void displayRooms() {
        for (int i = 0; i < totalRooms; i++) {
            cout << "Room " << i + 1 << ": " << rooms[i] << endl;
        }
    }
};

int main() {
    Hotel hotel(10); // Create a hotel with 10 rooms

    int choice;
    int roomNumber;

    while (true) {
        cout << "1. Book a room" << endl;
        cout << "2. Cancel a booking" << endl;
        cout << "3. Display rooms" << endl;
        cout << "4. Exit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                cout << "Enter room number: ";
                cin >> roomNumber;
                hotel.bookRoom(roomNumber);
                break;
            case 2:
                cout << "Enter room number: ";
                cin >> roomNumber;
                hotel.cancelBooking(roomNumber);
                break;
            case 3:
                hotel.displayRooms();
                break;
            case 4:
                return 0;
            default:
                cout << "Invalid choice. Please try again." << endl;
        }
    }

    return 0;
}
