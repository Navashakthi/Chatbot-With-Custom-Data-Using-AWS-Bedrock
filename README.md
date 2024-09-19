# Chatbot-With-Custom-Data-Using-AWS-Bedrock
Building a Chatbot that answers questions related to our data trained on top of LLM models using AWS-Bedrock

Modern chatbots serve as digital agents, offering 24/7 customer support across industries. They handle real-time, multilingual inquiries, provide data-driven insights, and scale easily, making them cost-effective. Powered by large language models (LLMs), chatbots understand conversational language but need thoughtful, personalized responses to be more than basic assistants. Integrating internal knowledge bases enables chatbots to deliver tailored, contextual replies. The Retrieval Augmented Generation (RAG) model enhances chatbot performance by grounding responses in factual data, reducing errors. Using Amazon Bedrock's Knowledge Bases with vector databases enables more personalized, relevant responses in this context.

#### Retrieval Augemented Generation
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

### Installation

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
