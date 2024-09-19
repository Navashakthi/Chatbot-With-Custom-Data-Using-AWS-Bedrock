# Chatbot-With-Custom-Data-Using-AWS-Bedrock
Building a Chatbot that answers questions related to our data trained on top of LLM models using AWS-Bedrock

Modern chatbots serve as digital agents, offering 24/7 customer support across industries. They handle real-time, multilingual inquiries, provide data-driven insights, and scale easily, making them cost-effective. Powered by large language models (LLMs), chatbots understand conversational language but need thoughtful, personalized responses to be more than basic assistants. Integrating internal knowledge bases enables chatbots to deliver tailored, contextual replies. The Retrieval Augmented Generation (RAG) model enhances chatbot performance by grounding responses in factual data, reducing errors. Using Amazon Bedrock's Knowledge Bases with vector databases enables more personalized, relevant responses in this context.

## Retrieval Augemented Generation
RAG is an approach to natural language generation that incorporates information retrieval into the generation process. RAG architecture involves two key workflows: data preprocessing 
through ingestion, and text generation using enhanced context.

![image](https://github.com/user-attachments/assets/e81b6cbb-a209-4a74-ac80-6c9e8ed49c03)

## Solution Overview
The solution in this example utilizes a chatbot built with a Streamlit application and incorporates the following AWS services:

- Amazon Simple Storage Service (Amazon S3) as the data source
- Knowledge Bases for Amazon Bedrock for data ingestion
- Amazon OpenSearch Serverless as a vector store to store text embeddings
- AWS Lambda as the API function to call the Knowledge Bases API

## Prerequisites
Before executing, ensure you have the following prerequisites:

- **AWS Account**: An active AWS account with permissions to use SageMaker, S3, and IAM services.
- **S3 Bucket:** An S3 bucket where training data and model artifacts will be stored.
- **IAM Role:** An IAM role with the necessary permissions for SageMaker to access S3 and ECR.
- **AWS CLI:** AWS CLI configured with your access and secret keys, and the region set.
- **AWS Bedrock:** AWS Bedrock access and IAM role to invoke models. Access to embedding models.
- **AWS Cloudformation:** AS IAM acess to create resources using cloudformation stack.

## Steps to Create KnowledgeBase and Lambda Layer
1. On the Amazon S3 console, choose **Buckets** in the navigation pane.
2. Click **Create bucket**.
3. Name the bucket ```knowledgebase-<*your-account-number*>```.
4. Leave all other bucket settings as default and choose **Create**. 
5. Navigate to the ```knowledgebase-<*your-account-number*>``` bucket. 
6. Choose Create folder and name it ```dataset```.
7. Leave all other folder settings as default and choose **Create**.
8. Navigate to the ```dataset``` folder
9. Drag and drop the Amazon annual reports, proxies and shareholder letters data files you downloaded earlier to this bucket and choose **Upload**.
10. Navigate back to the bucket home and choose **Create folder** to create a new folder and name it ```lambdalayer```.
11. Leave all other settings as default and create the folder.
12. Navigate to the lambdalayer folder.
13. Upload the knowledgebase-lambdalayer.zip file available under the /lambda/layer folder in the code base you cloned earlier and choose Upload. You will use this Lambda layer code later to create the Lambda function.
14. In the left panel of Bedrock dashboard, clik o knowledgebases and create new.
15. Add necessary IAM roles and data source locations that we set up in previous steps.
16. Leave the other settings to default and choose the embedding model as Titan Embedding G1 – Text
17. For Vector database, click on quick create a new vector store
18. Review and create knowledgebase. Once its ready sync the knowledgebase with the data source.
19. Create a cloudformation with the template in this repo cfn directory and use the knowledgebase ID you just created.
20. Once the resources in cloudformation is ready, our chatbot is ready to execute.

## Installation & Execution

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-repo/project-name.git
   cd project-name
   ```
2. **Install the necessary Python packages:**
   ```bash
   pip install boto3 streamlit
   ```
3. **Ensure AWS CLI is installed and configured on your machine:**
   ```bash
   aws configure
   ```
4. **Execute the chatbot.py script:**
   ```bash
    python -m streamlit run .\streamlit\chatbot.py
   ```

## Conclusion
This example highlighted the importance of contextual chatbots and the complexities of RAG architecture for data ingestion and text generation. It introduced how Knowledge Bases for Amazon Bedrock simplifies the process by providing a fully managed, serverless RAG system with a vector store. A solution architecture and sample code were provided to demonstrate how to create contextual chatbot responses. For further details, refer to the Amazon Bedrock Developer Guide and Knowledge Base APIs.
