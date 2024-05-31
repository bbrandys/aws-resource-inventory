<p align="center">
</p>

## AWS SSM Automation Runbook to Setup AWS Config with Amazon Athena and Grafana Cloud
An automated approach to AWS resource inventory observability with AWS Systems Manager, Config, Athena, and Grafana


### What does this cloudformation template do?
This template will deploy an SSM Automation runbook called **Resource-Inventory-Visualization** that can be used to set up AWS Config to be used with Amazon Athena and Grafana Cloud to visualize your AWS resources - cross-account and cross-region

## Running the Resource-Inventory-Visualization Automation Runbook

### Prerequisites
1.  Configure [Delivering Configuration Snapshot to an Amazon S3 Bucket](https://docs.aws.amazon.com/config/latest/developerguide/deliver-snapshot-cli.html) for AWS.
1.  Ensure access to your S3 Bucket that is used for AWS Config.
1.  The S3 Bucket Name used with AWS Config.
1.  [Grafana Cloud Account](https://grafana.com/products/cloud/) 
1.  Configure the [Athena Plugin](https://grafana.com/grafana/plugins/grafana-athena-datasource/) within your Grafana Cloud Instance 

### Input Parameters for the Resource-Inventory-Visualization Automation Runbook
* **ConfigDeliveryChannelName:** (Required) Name of your AWS Config Delievery Channel.  The default is set to the value of default.
* **ConfigS3BucketLocation:** (Required) AWS Config S3 Bucket Name, this is the name of your S3 Bucket you currently use for AWS Config. (ie, config-bucket-1234567891)
* **AutomationAssumeRole:** (Optional) The ARN of the role that allows Automation to perform the actions on your behalf.
* **DeleteConfigVisualization:** (Optional) Set this to true if you would like to delete the resources created to enable this solution. The default is set to false, which will set up the solution. 

## Creating Visuals in Grafana Cloud

The **Resource-Inventory-Visualization** Automation Runbook will create the below views and datasets within Amazon Athena.  

*   v_config_rules_compliance
*   v_config_resource_compliance
*   v_config_rds_dbinstances
*   v_config_iam_resources
*   v_config_ec2_vpcs
*   v_config_ec2_instances
*   v_config_resources

## Import the Dashboard JSON into Grafana Cloud

Download the Resource Inventory dashboard JSON file.

In Grafana, go to Dashboards and click New > Import. 
Upload the JSON file that you previously Downloaded. 

The dashboard will now populate with your resource inventory data. 

<Image Placeholder>

This dashboard is only a starting point—depending on what resources you want to visualize, you can add additional views in Athena, Additional Panels, and more dashboards in Grafana. 
