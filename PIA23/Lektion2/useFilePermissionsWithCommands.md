# Add folder and file and with permission set who can read it

In this lab we will create a folder with a file in /tmp and you will give a different user permissions to manage the file.
This lab will not have the commands you will need to run. To see all the commands look at lab useFilePermissionsWithCommands.md under Lektion2.

This lab should be done on your EC2 and depends on you having a secondary user on that EC2 aswell.

## Create folder
**As user ec2-user**

In / create a folder named salesreports.

**Solution**

```bash
sudo mkdir /salesreports
```

## Set ec2-user as owner

Set user ec2-user as the owner and groupowner of the new folder /salesreports


**Solution**

```bash
sudo chown ec2-user:ec2-user /salesreports
```

## Create salesreport
**As user ec2-user**

In /salesreport create file salesreport_2312

**Solution**

```bash
touch /salesreport/salesreport_2312
```

## Add report to salesreport_2312
**As user ec2-user**

With your selected text editor (nano or vim), add this report to the salesreport_2312 file

```bash
**Sales Report - December 2023**

*Overview:*
This report provides a summary of sales activities for the month of December 2023.

*Total Sales:*
Total Sales: $1,200,000

*Product-wise Breakdown:*
1. Product A: $450,000
2. Product B: $300,000
3. Product C: $200,000
4. Product D: $250,000

*Regional Performance:*
1. North Region: $500,000
2. South Region: $350,000
3. East Region: $200,000
4. West Region: $150,000

*Top Performing Sales Representatives:*
1. John Doe: $180,000
2. Jane Smith: $150,000
3. Mike Johnson: $120,000

*Sales Trends:*
- Overall sales increased by 15% compared to November 2023.
- Product A saw a significant boost in sales, contributing to the overall growth.
- The North Region outperformed other regions with a 10% increase in sales.

*Future Strategies:*
1. Focus on promoting Product A to leverage its popularity.
2. Invest in marketing campaigns targeting the West Region for improved performance.

*Upcoming Targets:*
Set a goal to achieve a 5% month-over-month growth in the first quarter of 2024.

*Conclusion:*
The sales team performed well in December 2023, and with strategic adjustments, we aim to continue this positive trend into the next quarter.

For detailed transaction data, refer to the attached spreadsheet.

```

**Solution**

```bash
nano /salesreports/salesreport_2312

Write or copy the text.

Save with ctrl + x and Y.
```

## Permissions for folder
**As user ec2-user**

Only ec2-user should be able to create and delete files in the directory /salesreports.

Your secondary user should be able to read the files in the directory.

Others should not be able to read the files in the directory.

**Solution**

```bash
sudo chown ec2-user:secondary_user /salesreports

sudo chmod 750 /salesreports
```

## Permissions for salesreport_2312
**As user ec2-user**

ec2-user should be able to write and read the file.

Your secondary user should be able to read the file.

Others should not have access to the file.

**Solution**

```bash
sudo chown ec2-user:testuser /salesreports/salesreport_2312

chmod 640 /salesreports/salesreport_2312
```

## Read salesreport_2312 as your secondary user
**As your secondary user**

Try and read the file /salesreport/salesreport_2312

**Solution**

```bash
less /salesreport/salesreport_2312
```
