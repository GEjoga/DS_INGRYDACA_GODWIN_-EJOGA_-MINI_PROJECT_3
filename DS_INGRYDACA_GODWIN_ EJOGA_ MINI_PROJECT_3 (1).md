## FILE HANDLING _ WORD COUNTER


```python
class WordCounter:
    def _init_(self, filename):
        self.filename = filename
        self.word_count = {}

    def process_file(self):
        with open(self.filename, 'r') as file:
            content = file.read()
            words = content.split()
            for word in words:
                word = word.strip('.,!?()[]{}"\'')
                word = word.lower()
                if word:
                    if word in self.word_count:
                        self.word_count[word] += 1
                    else:
                        self.word_count[word] = 1

    def display_word_frequency(self):
        print("Word frequency in the file:")
        for word, count in self.word_count.items():
            print(f"{word}: {count}")

def main():
    filename = "essay.txt"  # Replace with the actual filename
    counter = WordCounter(filename)
    counter.process_file()
    counter.display_word_frequency()

if __name__== "_main_":
    main()
```

## QUESTION 2 (AIR CONTROL SIMULATION: 


```python
class Flight:
    def _init_(self, flight_number, emergency=False):
        self.flight_number = flight_number
        self.emergency = emergency

class AirTrafficControl:
    def _init_(self):
        self.emergency_queue = deque()
        self.scheduled_queue = deque()

    def add_flight(self, flight):
        if flight.emergency:
            self.emergency_queue.append(flight)
        else:
            self.scheduled_queue.append(flight)

    def process_flights(self):
        print("Processing flights:")
        while self.emergency_queue:
            emergency_flight = self.emergency_queue.popleft()
            print(f"Emergency landing: Flight {emergency_flight.flight_number}")
        while self.scheduled_queue:
            scheduled_flight = self.scheduled_queue.popleft()
            print(f"Scheduled landing: Flight {scheduled_flight.flight_number}")

def main():
    atc = AirTrafficControl()

    atc.add_flight(Flight("ABC123"))
    atc.add_flight(Flight("XYZ789", emergency=True))
    atc.add_flight(Flight("DEF456"))
    atc.add_flight(Flight("GHI987", emergency=True))

    atc.process_flights()

if __name__ == "_main_":
    main()
```
