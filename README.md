# CSI Prediction on Intel Dev Cloud (Team Quixotic Sapiens - Intel AI Hackathon)
## What is our project about? ##
We have developed an AI-powered customer satisfaction analysis application for businesses leveraging call recordings as input data. This project revolutionises the way businesses understand and improve customer satisfaction by harnessing the power of artificial intelligence to analyze call recordings. By extracting valuable insights from customer interactions, the application aims to provide businesses with a comprehensive understanding of customer sentiments, concerns, and satisfaction levels. 

This analysis will enable businesses to identify patterns, trends, and areas for improvement in their customer service processes and interactions. By leveraging AI-driven sentiment analysis and other advanced techniques, the application seeks to streamline the process of CSI measurement, enabling businesses to proactively address customer needs, enhance customer experiences, and ultimately drive higher levels of satisfaction and loyalty.

## What is CSI? ##
Let's say you're a bank manager, and you want to know how satisfied your customers are with the services you provide. So, you might send out surveys asking questions like, "Were you satisfied with the speed of service?" or "Did our staff assist you well?"

Customers respond, giving their feedback. The bank then compiles this information to create a Customer Satisfaction Index (CSI). If the CSI is high, it means most customers are happy with the bank's services. But if it's low, it indicates there might be issues that need to be addressed, like long wait times or unfriendly staff.

So, just like you'd want to make sure your friends had a great time at a party you hosted, the bank wants to ensure their customers are happy with the banking experience. The CSI helps them gauge satisfaction levels
and make improvements where needed to keep customers coming back.

## Modules Used ##
We've made use of a variety of modules such as:
- **Intel® Neural Chat**
- **OpenAI Whisper**
- **SpeechBrain**
- **Streamlit**
- **Transformers (HuggingFace)**
- **Azure Communication Services (azure.communication.mail)**

## How do we implement it? ##

<p align="center">
  <img width="auto" height="auto" src="https://github.com/jayanzth/intel-ai-hackathon/assets/93752903/7bd5e14d-58c4-4d8b-b8c2-4e65d9c18cab">
</p>

1. **Call Audio**: The process begins with collecting call audio recordings, which serve as the primary input for the customer satisfaction analysis.

2. **Whisper & Speechbrain**: The call audio undergoes processing using tools like Whisper and Speechbrain. These tools are used to perform tasks such as Speech Transription, and Emotion Detection, corresponding to each timestamp.

3. **Prompt Template and Instructions**: After transcription, the instructions along with the previously generated inferences are compiled into a prompt template for further processing.

4. **LLM (Neural Chat)**: The prompt template is sent to the LLM (**Intel® Neural Chat**), which processes the given template, making use of the instructions provided earlier.
    <blockquote>
      example = "Communication: 8.5/10 Resolution: 8/10 Emotion Handling: 7/10. So, the overall Customer Satisfaction Index can be calculated as the average of these three scores, which is approximately 7.8/10."
    </blockquote>
    And the user template would be:
    <br><br>
    <blockquote>
      user_input = f"I will provide you with the transcripts of a customer service call. I will also provide you the tone of the voices at each timestamp.('a': Anger 'h': Happy 'n': Neutral) You have to analyse          both and come up with a Customer Satisfaction Index<Transcripts of the talks>\n{transcripts}<Transcripts of the talks\>\n<Tone and emotion of the voice>\n{emotions}<\Tone and emotion of the        voice>\n<Example>\n{example}<Example\>"
      </blockquote>

6. **Detailed Report**: The output from the LLM is further processed to generate a detailed report summarizing the analysis results. This report includes insights, trends, and recommendations derived from the conversation data, providing businesses with actionable information to improve customer satisfaction.

7. **Prompt (with inputs as Conversation Buffer and User Queries)**: Following the report generation, a new prompt is created based on the conversation buffer and any user queries. This prompt serves as input for the next stage of the flow, enabling continuous interaction and refinement of analysis outcomes.

8. **Chatbot**: The prompt is then fed into a chatbot, which interacts with users to address queries, provide additional information, or gather feedback.

9. **Answer**: Finally, the chatbot generates responses based on the input prompt, user queries, and conversation buffer, delivering answers or engaging in conversation to support ongoing analysis and decision-making. The user queries and inferences are sent back to the Conversation Buffer to maintain a feedback loop.

10. **Email**: Before the LLM analyses the emotions and transcripts as mentioned in (4), it checks if there's an issue with the attitude of the official and sends an email to the management using Azure communication service highlighting the issues.
  

## Cloud Architecture ##

We have our complete project running on Intel Dev Cloud Instance with the following specifications,
<p align="center">
  <img width="auto" height="auto" src="https://github.com/jayanzth/intel-ai-hackathon/assets/85375873/7d2e858e-8e60-41ad-869c-6ed7358b70ad">
</p>

Also we use Secure shell to forward the necessary ports from our VM to local machine.
<p align="center">
  <img width="auto" height="auto" src="https://github.com/jayanzth/intel-ai-hackathon/assets/93752903/cea74522-bab3-4d2b-a5db-75d35718acb9">
</p>

We forward port:8888 to access Jupyter notebooks for development and port:8501 for accessing streamlit UI.






