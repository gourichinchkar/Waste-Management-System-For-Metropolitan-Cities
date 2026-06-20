# Waste-Management-System-For-Metropolitan-Cities
Smart Waste Management System simulates IoT-enabled bins using Python. It monitors fill levels, triggers alerts when bins are full, and demonstrates smart city sustainability solutions without hardware. Easy to extend into web dashboards or real IoT sensors.

import random
import time

# Simulated Smart Waste Management System
class SmartBin:
    def __init__(self, bin_id, capacity=100):
        self.bin_id = bin_id
        self.capacity = capacity
        self.fill_level = 0

    def simulate_fill(self):
        # Randomly increase fill level
        self.fill_level += random.randint(5, 20)
        if self.fill_level > self.capacity:
            self.fill_level = self.capacity

    def is_full(self):
        return self.fill_level >= self.capacity

    def status(self):
        return {
            "Bin ID": self.bin_id,
            "Capacity": self.capacity,
            "Current Fill": self.fill_level,
            "Status": "FULL" if self.is_full() else "OK"
        }

# Main simulation
def run_simulation():
    bins = [SmartBin(bin_id=i) for i in range(1, 4)]  # 3 bins
    for cycle in range(10):  # simulate 10 cycles
        print(f"\nCycle {cycle+1}")
        for bin in bins:
            bin.simulate_fill()
            status = bin.status()
            print(status)
            if bin.is_full():
                print(f"ALERT: Bin {bin.bin_id} is FULL! Schedule pickup.")

        time.sleep(1)  # delay for simulation

if __name__ == "__main__":
    run_simulation()
