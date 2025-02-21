# booking-agent

Our objective is to create an LLM integrated with external APIs/functions which can fetch
real time data/insights and based on that information and then our LLM can generate
responses based on the information. LLMs with this type of flow are known as AI Agents.

I’ve used ollama to get the model weights which can be used for inference. Apart from that I’ve used langchain to integrate our LLM (which is downloaded from ollama), with API/function call, which is commonly known as tool calling.

Also the system prompt given to these LLMs also play a key role in how the final response will look like. Note that these models are prompt sensitive.
​
The whole structure of the code is like this:

![image](https://github.com/user-attachments/assets/cccb784e-3eb7-4e7a-84c9-58286c8754b8)

Output if tool calling happens:

![image](https://github.com/user-attachments/assets/5d202323-d19f-443b-9746-8fb061ed891c)

Output for general chat:

![image](https://github.com/user-attachments/assets/d6e373c7-94ee-456e-97ac-328cb5d2e5a0)

# Future scope of improvement:

1. Making the LLM more robust by adding the chat history functionality i.e. LLMs now
remembers all the previous conversations which have happened with a particular
user.

2.​ Currently the tool/function is a dummy function (code snippet attached below for
reference), we can connect it with DB and can share the latest information with the
user.
  ```py
  # Function which will be called if tool calling happens.​
  @tool​
  def book_room(name, contact_number, check_in_date, check_out_date,
  room_type)-> str:​
  """Book a hotel's room on behalf of the user."""​
  ​
  if(payment_done()):​
  ​
  ​ # update the DB that a room is booked.​
  ​ return f"Thanks {name}. Your {room_type} room has been booked
  and details will be shared to your contact number:
  {contact_number}."​
  return "Payment was not successful. Room wasn't booked."
  ```

3. Integration with website or hotel documents via RAG so that even staff can use it (better response generation for general hotel related queries).
