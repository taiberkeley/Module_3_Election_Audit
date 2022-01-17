# Module_3_Challenge - Election Audit

# 1.	Overview of Election Audit: 
The objective of the election audit analysis is to help Seth and Tom submit the election audit results to the election commission.

# 2.	Election-Audit Results: Using a bulleted list, address the following election outcomes. Use images or examples of your code as support where necessary.

# o	How many votes were cast in this congressional election?
The election had a total of 369,711 votes.
For that I’ve used the command below that counts how many lines the csv file has excluding the header
For each row in the CSV file.
    for row in reader:
    
        # Add to the total vote count
        total_votes = total_votes + 1

# o	Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct.

County Votes:
Jefferson: 10.5% (38,855)
Denver: 82.8% (306,055)
Arapahoe: 6.7% (24,801)

To achieve the result:
For each row in the CSV file
    for row in reader:
Extracted the county name from each row
        county_name = row[1]
Tracked the county's vote count
            county_votes[county_name] = 0 
Added a vote to that county's vote count
        county_votes[county_name] += 1
Printed the final county vote count to terminal
    election_results = (
        f"\nElection Results\n"
        f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        f"-------------------------\n\n"
        f"County Votes:\n\n")
    print(election_results, end="")

Saveed the results to our text file
with open(file_to_save, "w") as txt_file:
   
    txt_file.write(election_results)


# o	Which county had the largest number of votes?

Largest County Vote: Denver
To achieve the result:
Wrote an if statement to determine the winning county and get its vote count.

        if county_vote > largest_county_voter :
            largest_county = county
            largest_county_voter = county_vote

Printed the county with the largest turnout to the terminal
    largest_county = f"\nLargest County Vote: {largest_county}\n\nCandidates Votes:"
    print(largest_county)

Saved the county with the largest turnout to a text file.
    txt_file.write(largest_county)

# o	Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.
# o	Which candidate won the election, what was their vote count, and what was their percentage of the total votes?

Candidates Votes:
Charles Casper Stockham: 23.0% (85,213)
Diana DeGette: 73.8% (272,892)
Raymon Anthony Doane: 3.1% (11,606)
-------------------------
Winner: Diana DeGette
Winning Vote Count: 272,892
Winning Percentage: 73.8%


To achieve the result:

Created a candidates list and candidate votes dictionary
candidate_options = []
candidate_votes = {}

Tracked the winning candidate, vote count and percentage
winning_candidate = ""
winning_count = 0
winning_percentage = 0

Got the candidate name from each row.
candidate_name = row[2]

Added a vote to that candidate's count
candidate_votes[candidate_name] += 1

Retrieveed vote count and percentage
        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

 Determined winning vote count, winning percentage, and candidate
        if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage


Printed the winning candidate (to terminal)
    winning_candidate_summary = (
        f"-------------------------\n"
        f"Winner: {winning_candidate}\n"
        f"Winning Vote Count: {winning_count:,}\n"
        f"Winning Percentage: {winning_percentage:.1f}%\n"
        f"-------------------------\n")
    print(winning_candidate_summary)


Saved the winning candidate's name to the text file
    txt_file.write(winning_candidate_summary)

# 3.	Election-Audit Summary: 
The same script can be reused in another election. If the csv file follows the same pattern for the header (Ballot ID, County, Candidate) no initial modification needs to be made.
If the new election has a different csv file, they need to assign in which row the candidates and counties are located.
Also, it will be important to assign the new path for the csv and txt files for the next elections.
