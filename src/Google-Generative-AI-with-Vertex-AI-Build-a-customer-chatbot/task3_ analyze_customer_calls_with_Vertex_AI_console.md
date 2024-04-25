# Structured Prompt 

# Test data form 
### banking_dataset.csv file

# Context

Multi-choice problem: Define the category of the ticket?
Categories:
- Credit card
- Bank account services
- Loans and Mortgages


# Example For Training
### Example1
I lost my credit card numbered 12345. Can you help with deactivating the card? (input)
(out category =Credit card )


 ### Example2 
 I would like to change the address associated with my account. I have been calling the bank multiple times but couldn't get through. Please help me.
 (out category =Bank account serives)

 ### Example3
 good morning my name is xxxx xxxx and i appreciate it if you could help me put a stop to chase bank cardmember services. I wrote to chase asking for debt verification and what they sent me a statement which is not acceptable i am asking the bank to validate the debt instead i been receiving mail every month from them attempting to collect a debt i have a right to know this information as a consumer chase account xxxx xxxx xxxx xxxx thanks in advance for your help
(out category =Loans and Mortgages)


# Test Prompt1
Customer: Hello, I'm calling to ask about your auto loan rates.\nBank: Hi, thank you for calling [bank name]. We offer competitive auto loan rates. Would you like to get a quote? [Image of Auto loan]

# Response
Loans and Mortgages


# Test Prompt2
Customer: Hello, I'm calling to ask about your credit card rewards programs.\nBank: Hi, thank you for calling [bank name]. Can I have your name and customer ID, please?\nCustomer: Sure, my name is [customer name] and my customer ID is 1312345681.\nBank: Thank you, Mr./Ms. [customer name]. We offer a variety of credit card rewards programs to meet your needs. Would you like me to tell you more about them?

# Response 
Credit card


