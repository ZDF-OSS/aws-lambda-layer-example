# AWS Lambda Layer Example using AWS CDK (Python)

[![AWS Lambda](https://img.shields.io/badge/AWS-Lambda-orange?logo=amazon-aws)](https://aws.amazon.com/lambda/)
[![AWS CDK](https://img.shields.io/badge/AWS%20CDK-Python-blue?logo=amazon-aws)](https://aws.amazon.com/cdk/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

This project provides an example of how to create and deploy an **AWS Lambda Layer** using the **AWS Cloud Development Kit (CDK)** in **Python**.

## 📌 Overview

AWS Lambda Layers allow you to share libraries and dependencies across multiple Lambda functions. This example demonstrates how to:

- Define a Lambda Layer using **AWS CDK (Python)**.
- Package and deploy the layer to AWS.
- Use the layer in a Lambda function.

## 📂 Project Structure

```
aws-lambda-layer-example/
│── lambda_layer/                     # Directory for Lambda layer dependencies
│── cdk/                                # AWS CDK Infrastructure
│── requirements.txt                     # Python dependencies for CDK
│── cdk.json                             # CDK Configuration
│── README.md                            # This documentation
│── LICENSE
```

---

## 🚀 Prerequisites

- **AWS CDK** installed globally:  
  ```sh
  npm install -g aws-cdk
  ```
- **AWS CLI** configured with credentials:  
  ```sh
  aws configure
  ```
- **Python 3.8+** installed
- **Node.js 16+** (for AWS CDK)
- **Virtual Environment** setup (optional but recommended)

---

## 📦 Installation

Clone the repository:

```sh
git clone https://github.com/your-repo/aws-lambda-layer-example.git
cd aws-lambda-layer-example
```

Create a virtual environment and install dependencies:

```sh
python3 -m venv .venv
source .venv/bin/activate  # On Windows use .venv\Scripts\activate
pip install -r requirements.txt
```

Install AWS CDK dependencies:

```sh
cdk bootstrap
```


## 🚀 Deploying to AWS

### 1️⃣ **Synthesize the CloudFormation template**
This command generates a CloudFormation template for your AWS infrastructure.

```sh
cdk synth
```

### 2️⃣ **Deploy the Lambda Layer**
Deploy the stack that creates the Lambda Layer:

```sh
cdk deploy LambdaLayerStack
```

Once deployed, note the **Layer ARN** from the output.

### 3️⃣ **Deploy the Lambda Function**
Deploy the Lambda function using the Layer ARN:

```sh
cdk deploy LambdaFunctionStack --parameters LayerArn="arn:aws:lambda:region:account-id:layer:LayerName:Version"
```

Alternatively, modify `app.py` to automatically retrieve the layer ARN from `LambdaLayerStack`.

---

## 🔄 Updating the Lambda Layer

If you make changes to the layer, update it with:

```sh
cdk deploy LambdaLayerStack
```

Then, update functions that use it:

```sh
cdk deploy LambdaFunctionStack
```

---

## 📌 Testing the Lambda Function

### Invoke the function from the AWS CLI:

```sh
aws lambda invoke --function-name MyLambdaFunction output.json
cat output.json
```

### Check logs via AWS CloudWatch:

```sh
aws logs tail /aws/lambda/MyLambdaFunction --follow
```

---

## 🛠️ Cleanup

To delete the deployed resources and avoid AWS charges:

```sh
cdk destroy
```

---

## 📜 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---

## 📞 Contact & Support

For issues or contributions:
- Open an **issue** or **pull request** in this repository.
- Visit [AWS Lambda Documentation](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html).
- Contact us at [info@zerodotfive.com](mailto:kontakt@zerodotfive.com).
