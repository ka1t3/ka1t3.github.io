+++
date  = 2025-08-26
draft  = false
title  = 'Python skills (part 1)'
tags = ["Code", "Python"]
+++

## The reminder

A while ago, I was asked this question:

“Give the number of occurrences of IP addresses in this log file.” You need to count how many times each IP address appears in this txt file.

Example of file content:

```txt
192.168.1.1 - - [10/Oct/2025:13:55:36 +0200] "GET /index.html HTTP/1.1" 200 532
10.0.0.14 - - [10/Oct/2025:13:56:01 +0200] "POST /login HTTP/1.1" 403 143
192.168.1.1 - - [10/Oct/2025:13:56:25 +0200] "GET /favicon.ico HTTP/1.1" 200 324
172.16.0.7 - - [10/Oct/2025:13:57:00 +0200] "GET /about HTTP/1.1" 404 225
10.0.0.14 - - [10/Oct/2025:13:57:30 +0200] "GET /profile HTTP/1.1" 200 621
192.168.1.1 - - [10/Oct/2025:13:58:00 +0200] "GET /contact HTTP/1.1" 200 145
[]...[]
172.16.0.8 - - [10/Oct/2025:14:10:00 +0200] "GET /about HTTP/1.1" 404 225
10.0.0.10 - - [10/Oct/2025:14:10:10 +0200] "GET /profile HTTP/1.1" 200 621
192.168.1.2 - - [10/Oct/2025:14:10:30 +0200] "GET /contact HTTP/1.1" 200 145
172.16.0.9 - - [10/Oct/2025:14:10:52 +0200] "GET /support HTTP/1.1" 200 543
```

Well, my code was flawed, and i was unable to provide a clean answer.

That's when I realized I needed to brush up on my development basics. (I had forgotten and, more importantly, lost a lot of muscle memory...).
In another article, I'll talk about how i got into application security and, above all, what my role as Lead Application Security entails in a company with over 350,000 employees and more than 1,000 projects. But it's clear that I've moved away from development to focus more on AppSec strategy.

So here we go, it's time to rebuild my skills with the goal of developing as many skills as possible in security automation. Below is a link to a Github repo that contains all my notes on the courses i'm followed so that you can practice too.

The link : https://github.com/ka1t3/Python.git

As for the question from earlier, below is a solution from Gemini 2.5 pro:

```Python
import re
from collections import Counter
import os

def count_ip_occurrences(log_file_path):
    """
    Analyze a log file to count the occurrences of each IP address.

    Args:
        log_file_path (str): Path to the log file.

    Returns:
        collections.Counter: A Counter object containing the IPs and their counts,
                             or None if the file is not found.
    """
    # 1. Check if the log file exists before proceeding
    if not os.path.exists(log_file_path):
        print(f"Error: The file '{log_file_path}' was not found.")
        return None

    # 2. Define the regular expression (regex) to extract IP addresses (IPv4 format)
    #    - \b ensures that we capture a whole word (prevents matching part of a longer number)
    #    - (?:...) is a non-capturing group
    ip_pattern = re.compile(r'\b(?:[0-9]{1,3}\.){3}[0-9]{1,3}\b')

    try:
        # 3. Read the file and find all matches
        with open(log_file_path, 'r', encoding='utf-8') as file:
            # Read the entire content at once for global searching
            content = file.read()
            # re.findall returns a list of all strings that match the pattern
            ip_list = ip_pattern.findall(content)

        # 4. Use collections.Counter to count the list elements
        #    This is the simplest and most efficient method for this task.
        ip_counts = Counter(ip_list)
        return ip_counts

    except Exception as e:
        print(f"An error occurred while reading or processing the file: {e}")
        return None

# --- Script entry point ---
if __name__ == "__main__":
    # Name of the file containing the logs.
    # Make sure this file is in the same folder as the Python script,
    # or provide a full path (e.g., "C:/Users/YourName/Documents/logs.txt").
    LOG_FILE = 'apache_logs.txt'

    # Call the main function
    ip_occurrences = count_ip_occurrences(LOG_FILE)

    # 5. Display the results clearly
    if ip_occurrences:
        print(f"Analysis of the file '{LOG_FILE}' completed.")
        print("Number of occurrences for each IP address:")
        
        # The .most_common() method sorts results from most to least frequent.
        for ip, count in ip_occurrences.most_common():
            print(f"- {ip}: {count} times")
    else:
        print("No results to display due to an error or empty file.")

```

But there are slew of ways to do this, so try them out and have some fun.

**My alternative suggestion**
Add a line ip,timestamp,method,url,status,size and change the file extension to .csv to answer the question with pandas.

```Python
import pandas as pd

# Define count_entries()
def count_entries(csv_file, c_size, colname):
    """Return a dictionary with counts of
    occurrences as value for each key."""
    
    # Initialize an empty dictionary: counts_dict
    counts_dict = {}

    # Iterate over the file chunk by chunk (but not necessary for a small file)
    for chunk in pd.read_csv(csv_file, chunksize=c_size):

        # Iterate over the column in DataFrame
        for entry in chunk[colname]:
            if entry in counts_dict.keys():
                counts_dict[entry] += 1
            else:
                counts_dict[entry] = 1

    # Return counts_dict
    return counts_dict

# Call count_entries(): result_counts
result_counts = count_entries('logs.csv', 10, 'lang')

# Print result_counts
print(result_counts)
```

## The wod / practice

You will find slightly more advanced concepts on certain topics in my notes.
Personally, to avoid forgetting (again...) and getting confused, there is nothing better than practice. 
I break it down into two parts: a review of the fundamentals (spaced repetition principle), then I carry out projects in parallel to reinforce this knowledge.
I will write a specific blog post about the project I am currently working on (when I can find the time between my work, my children, my hobbies, and preparing for my certifications).

Overall, the internet is full of great content for building a solid foundation. 
For a completely free version, you can take these courses, which are a great place to start:


```
├── Calmcode : https://calmcode.io/ 
├── Futurecoder : https://futurecoder.io/
├── Automate boring stuff with Python : https://automatetheboringstuff.com/

```

For reviewing the fundamentals, i use this simple method (although it’s not the most suitable if the GitHub repo gets updated): load the file into an AI (I use a free plan i got with Perplexity) and ask it to propose exercises for you.

**Example of prompt**

Context:
- I have a Python code file that i will provide. This file contains [e.g., a class, utility functions, a script, etc.]. My goal is to learn and improve in Python by practicing directly on this code.

Request:
- Propose a series of progressive, practical exercises (between 5 and 10) directly related to the content of the file. The exercises should help me better understand, modify, and improve the provided code.

Output format:
- Numbered list of exercises.
- Each exercise should be written as a clear instruction (e.g., “Add a function that…”, “Modify the class to…”).
- Indicate the difficulty level for each exercise (Beginner, Intermediate, Advanced).
- Provide an expected learning objective (e.g., “Understand inheritance”, “Practice loops”, “Handle files”).

What you should not do:
- Do not provide the solutions or corrected code directly.
- Do not suggest exercises unrelated to the provided file.
- Do not be too vague (each exercise must be actionable).
- Do not propose tasks that are impossible or unsuitable for the current code level.

Another method is to use Gitinjest [Gitinjest](https://gitingest.com/) to better feed your LLM and therefore interact more effectively with the code.

A bientôt !
