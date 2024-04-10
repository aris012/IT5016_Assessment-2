## IT5016_Assessment 2_
#### 20240394 - Aristoteles B. Biadora Jr.

### Software Development Life Cycle (SDLC)

#### Planning
###### What is the client need:
  *	Create a Help Desk Ticketing System Prototype
  *	Help Desk ticketing system should handle tickets from internal customers.
  *	Assistance from the help desk by staff members
###### What is the goal:
  *	Make a ticketing system prototype.
  *	Solve the ticket problem, issue containing password change should be generated.
  *	Provide a feedback response. 

##### Requirement Analysis

#####  Defining the ticketing system:
###### Gathering the following information:
  *	Staff ID
  *	Ticket Creator name 
  *	Contact Email
  *	Description of the issue
###### Statistics:
  *	Keep Track of:
    *	Number ticket submitted.
    *	Number of resolved tickets.
    *	Number of open tickets.
    *	A way to display those statistics to the console.	
###### Technical Requirement:

  * Common Ticket Information.
  * Allow staff to make ticket and IT team to respond to the ticket, resolve, reopen and provide response to the ticket.   * Method for resolving password change requests.
  * Method to print information ticket objects.
  * Method ticket class should contain info on ticket statistics, return statistic information.
  * The Main Method
  * Display Ticket Statistics


### Solution Design Stage

###### “Displaying Ticket Statistics:”

Tickets Created: - Track of number of tickets submitted.

Tickets Resolved: - Track of Resolved tickets.

Tickets to solve: - Track of Open tickets, that are needed to solve.

###### “Printing Tickets:”

Ticket Number: - Automatically assigned number starting with “2000”

Ticket Creator: - User input providing the name of the creator.

Staff ID: - User input providing by the user’s staff ID.

Email Address: - User input providing user’s email address.

Description: - User input providing the description of the user’s issue. 
(If the request input to the description is “Password Change”, generate a new password for the user.)

Response: - After submitting the ticket, to respond to a ticket by providing a feedback response. Default response can be set as “Not Yet Provided”.

Ticket Status: - Response from the IT department and ticket status should be open, closed or reopened.


### Development Stage
##### Writing the Code:
###### Tickets array

        open_tickets = []
        closed_tickets = []
        reopened_tickets = []
        ticket_number = 2000

#### Creating ticket user input

        def create_ticket(ticket_number):
            staff_id = input("Staff ID: ")
            creator_name = input("Ticket creator name: ")
            contact_email = input("Contact email: ")
            issue_description = input("Description of the issue: ")

            if issue_description.lower() == "password change":
                new_password = staff_id[:2] + creator_name[:3]
                status = "Closed" 
                response = f"New generated password: {new_password}"
            elif issue_description.lower() == "My monitor stoppped working":
                status = "Closed"
                response = f"The monitor has been replaced"
            else:
                status = "Open"
                response = "Not Yet Provided"

            ticket_details = {
                "Ticket Number": ticket_number,
                "Staff ID": staff_id,
                "Ticket Creator": creator_name,
                "Email address": contact_email,
                "Description": issue_description,
                "Response": response,
                "Status": status
            }

            return ticket_details

##### Display ticket statistics with the use of lenght function

        def display_ticket_statistics():
            total_tickets_created = len(open_tickets) + len(closed_tickets) + len(reopened_tickets)
            total_tickets_resolved = len(reopened_tickets) + len(closed_tickets)
            total_tickets_solved = len(open_tickets)
            print("Tickets Created:", total_tickets_created)
            print("Ticket Resolved:", total_tickets_resolved)
            print("Ticket to Solve:", total_tickets_solved)

##### Print ticket lists with use of loop method

        def print_tickets(ticket_list):
            for ticket in ticket_list:
                print()
                print("Ticket Number:", ticket["Ticket Number"])
                print("Staff ID:", ticket["Staff ID"])
                print("Ticket Creator:", ticket["Ticket Creator"])
                print("Email address:", ticket["Email address"])
                print("Description:", ticket["Description"])
                print("Response:", ticket["Response"])
                print("Status:", ticket["Status"])
                print()

        while True:
            print()
            print("HELP DESK TICKETING SYSTEM")
            print()
            ticket_number += 1
            ticket = create_ticket(ticket_number)
            if ticket["Status"] == "Closed":
                closed_tickets.append(ticket)
            elif ticket["Status"] == "Resolved":
                reopened_tickets.append(ticket)
            else:
                open_tickets.append(ticket)

            print(f"Ticket {ticket_number} created successfully!")
            print()
            print("Display Ticket Statistics")
            display_ticket_statistics()
            print()
            print("Printing Tickets")
            print()
            all_tickets = open_tickets + closed_tickets + reopened_tickets
            all_tickets_sorted = sorted(all_tickets, key=lambda x: x["Ticket Number"])
            print_tickets(all_tickets_sorted)




### Testing
#### Output of Development Stage:

Display Ticket Statistics

<br>

Tickets Created: 3

Ticket Resolved: 1

Ticket to Solve: 2


<br>

Printing Tickets


<br>

Ticket Number: 2001

Staff ID: ARISBIADORA

Ticket Creator: Aristoteles

Email address: arisbbiadora12@gmail.com

Description: password change

Response: New generated password: ARAri

Status: Closed



<br>



Ticket Number: 2002

Staff ID: JOYCEJAVIER

Ticket Creator: Joyce Eirene Javier

Email address: joyceeirenejavier@gmail.com

Description: Monitor is slow

Response: Not Yet Provided

Status: Open


<br>



Ticket Number: 2003

Staff ID: ALLANALVAREZ

Ticket Creator: Allan Paul Alvarez

Email address: allanpaulalvarez@gmail.com

Description: No Internet

Response: Not Yet Provided

Status: Open


<br>


HELP DESK TICKETING SYSTEM




<br>


#### References

(2024, April 10). Retrieved from Code Review: https://codereview.stackexchange.com/questions/263171/ticketing-program-using-python-3

(2024, April 10). Retrieved from Python: https://docs.python.org/3/tutorial/errors.html

Loops, M. (2024, April 10). Retrieved from Whitecliffe Canvas: https://learn.mywhitecliffe.com/courses/1471/pages/while-loops?module_item_id=72433

Module, I. S. (2024, 10 04). Retrieved from Whitecliffe Canvas: https://learn.mywhitecliffe.com/courses/1471/pages/if-statements?module_item_id=72427

Scenario, A. (2024, April 10). mywhitecliffe assignment. Retrieved from https://learn.mywhitecliffe.com/courses/1471/assignments/12851

Statements, M. E. (2024, April 10). Retrieved from Whitecliffe Canvas: https://learn.mywhitecliffe.com/courses/1471/pages/if-elif-statements?module_item_id=72429

Whitecliffe, M. E. (2024, April 10). Retrieved from Whitecliffe Canvas: https://learn.mywhitecliffe.com/courses/1471/pages/more-on-exceptions?module_item_id=72464

Whitecliffe, M. F. (2024, April 10). Retrieved from Whitecliffe Canvas: https://learn.mywhitecliffe.com/courses/1471/pages/for-loops?module_item_id=72436

Whitecliffe, M. F. (2024, April 10). Retrieved from Whitecliffe Canvas: https://learn.mywhitecliffe.com/courses/1471/pages/functions-with-parameters?module_item_id=72447

Whitecliffe, M. L. (2024, April 10). Retrieved from Whitecliffe Canvas: https://learn.mywhitecliffe.com/courses/1471/pages/lists?module_item_id=72437

Whitecliffe, M. R. (2024, April 10). Retrieved from Whitecliffe Canvas: https://learn.mywhitecliffe.com/courses/1471/pages/returning-data-from-functions?module_item_id=72449

Whitecliffe, M. W. (2024, April 10). Retrieved from Whitecliffe Canvas: https://learn.mywhitecliffe.com/courses/1471/pages/while-loops?module_item_id=72433








