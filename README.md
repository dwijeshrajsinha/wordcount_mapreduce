# Exp 02 Word Count using MapReduce

**Date:08/08/2026**

## AIM:
To implement the Word Count program using the MapReduce programming model and determine the frequency of each word in the given input text.

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create a Python/Java project in the preferred IDE (Eclipse/IntelliJ IDEA/VS Code).

### Step 3:
Create the Python/Java program for the Word Count application using the MapReduce concept.

### Step 4:
Implement the **Mapper** phase to read the input text and emit each word as a key with a value.

### Step 5:
Implement the **Shuffle and Sort** phase to group identical words together.

### Step 6:
Implement the **Reducer** phase to sum the values associated with each word and calculate its total frequency.

### Step 7:
Compile and execute the program.

### Step 8:
Verify and display the word frequencies.

## PROGRAM:
```
text = """
hello world
hello python
world of python
"""

def mapper(text):
    result = []

    words = text.lower().split()

    for word in words:
        result.append((word, 1))

    return result



def shuffle_sort(mapped_data):
    grouped = {}

    for word, count in mapped_data:
        if word not in grouped:
            grouped[word] = []

        grouped[word].append(count)

    
    return dict(sorted(grouped.items()))



def reducer(grouped_data):
    result = {}

    for word, counts in grouped_data.items():
        result[word] = sum(counts)

    return result



mapped = mapper(text)

print("Mapper Output:")
print(mapped)


shuffled = shuffle_sort(mapped)

print("\nShuffle & Sort Output:")
print(shuffled)

final_result = reducer(shuffled)

print("\nReducer Output:")
for word, count in final_result.items():
    print(word, ":", count)
```

## OUTPUT:
<img width="810" height="240" alt="image" src="https://github.com/user-attachments/assets/37cfab94-e3cd-4638-9215-9ac8ba73a9b2" />
## RESULT:

The Word Count program using the MapReduce programming model was implemented successfully, and the frequency of each word in the given input text was computed correctly.
