# {fa}`square-check fa-regular` Choosing the Right Compute Orchestration Tool for Your Research Workload
  This article provides a detailed comparison of AWS Batch and AWS ParallelCluster, focusing on their architectural differences, scalability models, and suitability for distributed data processing versus tightly coupled HPC simulations. It helps in understanding which service is best for different research workloads. 
  
## Link
https://aws.amazon.com/blogs/hpc/choosing-the-right-compute-orchestration-tool-for-your-research-workload/

## Highlights
- <a href="https://aws.amazon.com/hpc/parallelcluster/">AWS ParallelCluster</a> is a flexible tool for building and managing HPC clusters on AWS. It’s ideal for tightly coupled workloads, like running simulations or analytics that require a traditional HPC cluster.
- Figure 1 – Overview of AWS ParallelCluster and its components for HPC workloads. Integration with Slurm and Amazon EC2 right-sizes compute node numbers based on the job queue. Amazon FSx for Lustre allows for access to a high-performance file system while also taking advantage of Amazon S3 object storage. All of this is connected using Elastic Fabric Adapter (EFA) which provide extremely high-performance connectivity and scaling for tightly-coupled workloads.
  -  ![Figure 1](https://firebasestorage.googleapis.com/v0/b/tagr-prod.appspot.com/o/notespace%2Frobwarden27%40gmail.com%2Fuploads%2F2025-06-18T13%3A35%3A06.734Z-image.png?alt=media&token=7cc73e26-23c1-495e-92d1-4ad9b9f45b6f) 
- <a href="https://aws.amazon.com/batch/">AWS Batch</a> is suited for highly parallel, container-based jobs, including tightly-coupled workloads
- AWS Batch leverage existing containerized applications
- Figure 2 – AWS Batch workflow illustrating container-based job processing and integration with AWS services. Compatibility with Amazon EKS and ECS allows for flexibility at the Compute Environment layer.
  -  ![Figure 2](https://firebasestorage.googleapis.com/v0/b/tagr-prod.appspot.com/o/notespace%2Frobwarden27%40gmail.com%2Fuploads%2F2025-06-18T13%3A36%3A09.422Z-image.png?alt=media&token=35e825be-5425-4af7-bb49-29fc65685397) 
- <a href="https://aws.amazon.com/sagemaker/">Amazon SageMaker</a> is ideal for machine learning workloads, especially those developed in Jupyter Notebooks
- SageMaker provides a managed ecosystem of ML and data science tools, covering the entire spectrum from data discovery and exploration to model training and deployment.
- SageMaker also contains pre-trained models, allowing researchers to jump-start their ML projects
- Figure 3 – <a href="https://aws.amazon.com/pm/sagemaker">Amazon SageMaker</a> ecosystem showcasing high-level end-to-end process from data preparation to model deployment. Integrates with services like <a href="https://aws.amazon.com/efs/">Amazon EFS</a> for a local file system in notebooks and also with highly-optimized AWS Deep Learning Containers for training models.
  -  ![](https://firebasestorage.googleapis.com/v0/b/tagr-prod.appspot.com/o/notespace%2Frobwarden27%40gmail.com%2Fuploads%2F2025-06-18T13%3A37%3A55.964Z-image.png?alt=media&token=6ca1c7eb-9e6d-46b4-bd05-75bc24f0df35) 
- SageMaker, Batch, and ParallelCluster can all use Spot Instances to take advantage of their favorable economics. In the case of Spot Instances, you’ll need to verify that your workload can tolerate interruptions from reclaimed capacity
- generally speaking – it’s worthwhile to see if you can use Spot or Fargate with AWS orchestration tools for your research.
- <a href="https://aws.amazon.com/hpc/res/">Research and Engineering Studio on AWS</a> (RES) is an open-source web-based portal for administrators to create and manage secure, cloud-based research and engineering environments.
- <a href="https://aws.amazon.com/healthomics/">AWS HealthOmics</a> is a comprehensive solution for bioinformatics work. It facilitates raw genomic storage and processing, allowing researchers to store and analyze genomic data. It supports popular bioinformatics workflow definition languages like WDL and Nextflow, enabling researchers to process and analyze genomic data efficiently.
- Figure 6 – AWS HealthOmics platform structure highlighting genomic data processing and analysis capabilities. Raw sequence and reference data can be processed through Nextflow or WDL workflows and then analyzed via AWS analytics services such as <a href="https://aws.amazon.com/athena/">Amazon Athena</a>.
  -  ![](https://firebasestorage.googleapis.com/v0/b/tagr-prod.appspot.com/o/notespace%2Frobwarden27%40gmail.com%2Fuploads%2F2025-06-18T13%3A38%3A24.941Z-image.png?alt=media&token=10e1cc40-bbfc-4875-a45b-2ca5bde5b2bd) 
- researchers have been using serverless computing to speed up embarrassingly parallel workloads, too – including ML hyperparameter optimization, genome search, and even MapReduce.
- <a href="https://aws.amazon.com/lambda/">AWS Lambda</a> is a serverless interface for running code without managing servers. It’s designed for loosely coupled workloads, allowing researchers to run code in response to events like changes in data (or the arrival of data). Lambda scales automatically, enabling you to run thousands of concurrent executions.
  - :::{note}
      Gonna need to look up loosely coupled vs. tightly coupled workloads. It seems important to this decision.
    :::
- Lambda, combined with Step Functions, is useful for workloads that involve different compute steps, data needs, and may even require decision gates or human input.
- Figure 7 – Illustration of a sample serverless computing architecture: a data stream of jobs to be processed is picked up by AWS Lambda and put into a downstream <a href="https://aws.amazon.com/sqs/">Amazon SQS</a> queue. AWS Step Functions then reads from this queue and handles the heavy lifting of distributed compute orchestration via Lambda worker functions. Step Functions also leverages <a href="https://aws.amazon.com/dynamodb/">Amazon DynamoDB</a> for workload state management, event handling with <a href="https://aws.amazon.com/eventbridge/">Amazon EventBridge</a> and storing processed results in Amazon S3.
  -  ![](https://firebasestorage.googleapis.com/v0/b/tagr-prod.appspot.com/o/notespace%2Frobwarden27%40gmail.com%2Fuploads%2F2025-06-18T13%3A38%3A52.908Z-image.png?alt=media&token=8dbb5675-ac3c-4447-b0a4-d2910ecefe07) 
- Choosing the right AWS compute orchestration tool is not about finding a one-size-fits-all solution but about aligning the tool’s capabilities with the specific requirements of your workload. The nuances of your project, the nature of your data, and your computational needs _should_ guide your decision.
- We recommend consulting with your research team and AWS account team to help you make the best decision for your project.
