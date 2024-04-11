## Assessment 2 Software Project Python Code 
### Help Desk Ticketing System Prototype
#### ReadMe file with instructions

#### Tickets array 
##### This where we store number of open, closed and reopened tickets, with the ticket number value 2000.

        open_tickets = []
        closed_tickets = []
        reopened_tickets = []
        ticket_number = 2000

#### Creating ticket user input 
##### With the function input() and def () and the use of "if" "elif and "else" for the description issue

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

#### Ticket Details
##### Here is the code for the ticket details with the return statement

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

#### Display Ticket Statistics 
##### Here with the use of lenght function, to count all the ticket created, resolbed and solve.

          def display_ticket_statistics():
              total_tickets_created = len(open_tickets) + len(closed_tickets) + len(reopened_tickets)
              total_tickets_resolved = len(reopened_tickets) + len(closed_tickets)
              total_tickets_solved = len(open_tickets)
              print("Tickets Created:", total_tickets_created)
              print("Ticket Resolved:", total_tickets_resolved)
              print("Ticket to Solve:", total_tickets_solved)

#### Print ticket lists with use of loop method
##### With the use of 'for loop' for user's input 'for' 'in' statament to dsiplay all ticket, I also used 'while loop' to allow code execute repeatedly.

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

#### Output of the printing ticket display statistics.
##### Here is code part for printing the output with the use of key=lambda for the ascending of the ticket number, with all the ticket sorted out. 

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

##### Final code for Assessement 2.



