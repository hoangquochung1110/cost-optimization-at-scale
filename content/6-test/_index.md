---
title : "Solution Testing"
date : "2025-05-14"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

We will create an EBS volume with type gp2 to test the solution:

1. Sign in again using a member account.  
   ![Member account](/images/5.conformancepack/019-memberaccount.png)

2. Navigate to the EC2 service.

3. In the left navigation pane, select **Volumes**.  
   ![EC2 Console](/images/6.test/002-test.png)

4. Create a new volume with the following properties, making sure to choose the **gp2** volume type.  
   ![Create EBS Volume](/images/6.test/003-test.png)

5. After creation succeeds, verify the volume state, then navigate to AWS Config.  
   
   💡 Note the EBS volume ID to correlate with the AWS Config Conformance Pack evaluation results.  
   ![Create EBS Volume](/images/6.test/004-test.png)

6. Select the Conformance Pack named `Cost-Optimization` (or similar).  
   ![AWS Config Conformance Pack](/images/6.test/005-test.png)

7. Click **View** to see the list of rules.  
   
   Since the newly created EBS volume is gp2 and unattached to any EC2 instance, two rules will be marked as noncompliant.  
   ![AWS Config Conformance Pack rule](/images/6.test/006-test.png)

8. Click the `CostOpt-Ebs-Gp3` rule to open the rule dashboard.  
   
   The dashboard lists EBS volumes violating the gp3 requirement, showing the same ID as our new volume.  
   ![AWS Config Conformance Pack rule](/images/6.test/007-test.png)

9. To remediate, click the **Remediate** button.

10. Wait a moment, then check the **Status** column as shown below:  
    ![AWS Config Conformance Pack rule](/images/6.test/008-test.png)  
   
    The EBS volume will disappear from the dashboard once it becomes compliant.

11. Verify the properties of the updated EBS volume:  
    ![EBS Volume](/images/6.test/009-test.png)
