# Cross-Account VPC Connection: Public VPC to Private VPC

This repository demonstrates how to establish a secure connection between two VPCs hosted in separate AWS accounts. One VPC is public, while the other is private. The connection setup uses **VPC Peering** to enable seamless communication between resources in the two VPCs.

---

## Features

- **Two VPCs in different AWS accounts**:
  - **Public VPC**: Resources accessible over the internet.
  - **Private VPC**: Resources not directly accessible over the internet.
- Secure connection using **VPC Peering**.
- CIDR block planning to avoid overlapping IP ranges.
- Configuration of route tables and security groups for cross-VPC communication.

---

## Architecture Diagram

```plaintext
Account A (Public VPC)           Account B (Private VPC)
+------------------------+        +-----------------------+
|  Public VPC            |        | Private VPC          |
|  CIDR: 172.17.0.0/16     |        | CIDR: 192.168.0.0/24 |
|  +------------------+  |        | +------------------+  |
|  | EC2 Instances    |  |        | | EC2 Instances    |  |
|  +------------------+  |        | +------------------+  |
+------------------------+        +-----------------------+
```
 Connection via VPC Peering

## Setup Guide

# Step 1: Create Public VPC (Account A)
### 1.Log in to Account A.
### 2.Create a VPC with CIDR block 172.17.0.0/23.

![Screenshot from 2024-12-28 23-07-18](https://github.com/user-attachments/assets/c2880f7a-cb24-4114-9229-2b03c139d983)
![Screenshot from 2024-12-28 23-08-29](https://github.com/user-attachments/assets/e6f74efb-70ef-4d26-afe7-331e065c878e)
![Screenshot from 2024-12-28 23-08-48](https://github.com/user-attachments/assets/b2162aa4-4468-48cb-82ca-3a6f0292b52b)

___

### 3.Add a public subnet and an internet gateway.

![Screenshot from 2024-12-28 23-08-53](https://github.com/user-attachments/assets/5c396603-d721-4cae-b9af-11e9934e5825)
![Screenshot from 2024-12-28 23-10-10](https://github.com/user-attachments/assets/2117c76b-b1d2-41d2-8bee-1e9241059160)
![Screenshot from 2024-12-28 23-10-21](https://github.com/user-attachments/assets/25aababc-3163-458c-81c5-4755edde1ecc)

![Screenshot from 2024-12-28 23-10-27](https://github.com/user-attachments/assets/5408a18c-67e7-48b4-a24f-169420050ea9)
![Screenshot from 2024-12-28 23-10-39](https://github.com/user-attachments/assets/916d92e9-2b24-4939-acaa-8130046196f2)
![Screenshot from 2024-12-28 23-10-44](https://github.com/user-attachments/assets/c4caab15-9273-4e40-9f3a-7b52ab6bbda3)

![Screenshot from 2024-12-28 23-10-54](https://github.com/user-attachments/assets/274ad359-2f95-441e-82a2-fb15e1e9b55c)
![Screenshot from 2024-12-28 23-11-07](https://github.com/user-attachments/assets/7c0cf382-4f8e-496b-8722-7379d3549ef8)

___

### 4.Attach the internet gateway to the VPC.

![Screenshot from 2024-12-28 23-11-25](https://github.com/user-attachments/assets/5b1d3b4c-bc0a-4f9e-b760-8eefa5fed061)
![Screenshot from 2024-12-28 23-11-33](https://github.com/user-attachments/assets/27c8639a-40d5-409b-8080-e0de140a81df)

___
 
### 5.Update the route table to allow internet access for the public subnet.  

![Screenshot from 2024-12-28 23-13-22](https://github.com/user-attachments/assets/ba7f1e94-3365-462a-8f22-3a654aa6d237)
![Screenshot from 2024-12-28 23-13-30](https://github.com/user-attachments/assets/8ed24556-c242-443a-83ef-27e8bb7edacf)


![Screenshot from 2024-12-28 23-16-07](https://github.com/user-attachments/assets/938d6c7c-d9c4-4057-81a1-2f91e8dfc7d1)
![Screenshot from 2024-12-28 23-16-37](https://github.com/user-attachments/assets/4ff4fc18-4d9a-4951-a743-7fe1b04b56ee)
![Screenshot from 2024-12-28 23-16-44](https://github.com/user-attachments/assets/0882ce04-1e16-46c1-b23a-5bbd12729a45)

___

### 6.Launch EC2 instances in the public subnet.
![Screenshot from 2024-12-28 23-20-17](https://github.com/user-attachments/assets/b9d079a3-e630-4cc7-99f4-bac34c6c4448)
![Screenshot from 2024-12-28 23-20-39](https://github.com/user-attachments/assets/4b62b201-a1dc-4c1f-91b1-a453a810a1c9)
![Screenshot from 2024-12-28 23-21-37](https://github.com/user-attachments/assets/34bb3ac8-0c8a-4b2d-89a7-fb1627d50999)
![Screenshot from 2024-12-28 23-22-00](https://github.com/user-attachments/assets/fb74600b-a06c-42fa-ac7a-5aee0807ab1d)
![Screenshot from 2024-12-28 23-22-25](https://github.com/user-attachments/assets/88856aeb-51ed-4ddf-8f8c-1876c02653c0)



# Step 2: Create Private VPC (Account B)
### 1.Log in to Account B.
### 2.Create a VPC with CIDR block 192.168.0.0/24.

![Screenshot from 2024-12-28 23-24-44](https://github.com/user-attachments/assets/468867af-4d9a-4039-88b5-b68780d3f0fb)
![Screenshot from 2024-12-28 23-25-27](https://github.com/user-attachments/assets/48c9693f-e598-464e-9533-c6d09f503c54)
![Screenshot from 2024-12-28 23-25-52](https://github.com/user-attachments/assets/5a763e7d-7d99-496f-bdeb-0206a59239ad)

___

### 3.Add private subnets.

![Screenshot from 2024-12-28 23-25-59](https://github.com/user-attachments/assets/da8d92c5-45b5-4abd-ba2c-2a792be17692)
![Screenshot from 2024-12-28 23-28-03](https://github.com/user-attachments/assets/7cd50645-7f3b-4ac6-9111-56dc301a7bd2)
![Screenshot from 2024-12-28 23-28-11](https://github.com/user-attachments/assets/4d613054-cb42-49ef-93a7-32078181a450)

![Screenshot from 2024-12-28 23-28-21](https://github.com/user-attachments/assets/7e23fb20-2ce9-4e4b-90fc-0b2f46c57f07)
![Screenshot from 2024-12-28 23-28-45](https://github.com/user-attachments/assets/d28d746b-d306-4c4e-8c94-b6abeb2e6fc2)
![Screenshot from 2024-12-28 23-28-56](https://github.com/user-attachments/assets/bed449c7-85b6-4770-874c-b8ba5b23ec65)
![Screenshot from 2024-12-28 23-29-12](https://github.com/user-attachments/assets/8ae64ed8-d643-4dab-a0a5-29ed54ea3e7c)
![Screenshot from 2024-12-28 23-29-53](https://github.com/user-attachments/assets/8fa032d9-c831-4b5c-908e-e5508fd3604f)

___

### 4.Launch EC2 instances in the private subnet.

![Screenshot from 2024-12-28 23-30-11](https://github.com/user-attachments/assets/4d8cf0fa-d3fd-494e-8bb3-b1784bbcdc9f)
![Screenshot from 2024-12-28 23-30-23](https://github.com/user-attachments/assets/ce944899-b43d-4586-a1d0-9fe56e81435c)
![Screenshot from 2024-12-28 23-30-52](https://github.com/user-attachments/assets/b2c00bad-c7aa-4564-94bb-772596d4cc53)
![Screenshot from 2024-12-28 23-31-28](https://github.com/user-attachments/assets/8a4e549b-1bb9-4141-ba10-59e5443416c1)
![Screenshot from 2024-12-28 23-32-01](https://github.com/user-attachments/assets/b35b3a5e-db41-4109-a19d-e4ed4b66a3e3)

___

![Screenshot from 2024-12-28 23-32-55](https://github.com/user-attachments/assets/e8b10a31-5043-4ab5-a7b6-94b0bebaf888)



# Step 3: Establish VPC Peering

### 1.In Account A, create a VPC peering connection targeting the VPC in Account B.

![Screenshot from 2024-12-28 23-33-51](https://github.com/user-attachments/assets/8ec64fe5-050b-42b3-b9e1-46aca6d405b7)
![Screenshot from 2024-12-28 23-36-15](https://github.com/user-attachments/assets/b9d40b56-4eae-42a8-86df-e2acc17e9707)
![Screenshot from 2024-12-28 23-36-37](https://github.com/user-attachments/assets/b12b3f87-3b61-4495-ace7-3cbb8594a482)

![Screenshot from 2024-12-28 23-37-02](https://github.com/user-attachments/assets/283a6012-e83a-4510-8738-f3274ae9c111)

___

### 2.In Account B, accept the VPC peering connection.

![Screenshot from 2024-12-28 23-37-11](https://github.com/user-attachments/assets/a727fb2a-b9a2-4f9d-8657-93e446442a3e)
![Screenshot from 2024-12-28 23-37-31](https://github.com/user-attachments/assets/40bc4f52-809e-44af-9ee6-c5f3f74f1719)



# Step 4: Configure Route Tables
### 1.In Account A, update the route table to route traffic for 192.168.0.0/25 through the peering connection.

![Screenshot from 2024-12-28 23-43-46](https://github.com/user-attachments/assets/b0cb4f7b-e808-45f1-88b1-361b0d7e6837)

___

![Screenshot from 2024-12-28 23-45-24](https://github.com/user-attachments/assets/aafd9a55-f116-455f-a7c5-dad480f21f61)
![Screenshot from 2024-12-28 23-45-57](https://github.com/user-attachments/assets/ac1fdf09-efdc-4b42-baa3-0b6f80e49289)
![Screenshot from 2024-12-28 23-46-06](https://github.com/user-attachments/assets/8ce8893a-4e89-441f-8dfa-47061de05f7f)

___

### 2.In Account B, update the route table to route traffic for 172.17.0.0/23 through the peering connection.

![Screenshot from 2024-12-28 23-47-10](https://github.com/user-attachments/assets/9cbfae83-361d-4a10-b7c4-4865c5c5103a)

___

![Screenshot from 2024-12-28 23-47-32](https://github.com/user-attachments/assets/70ac6740-3e30-410b-9d61-b5ee242aa029)
![Screenshot from 2024-12-28 23-48-03](https://github.com/user-attachments/assets/95ea4963-3c77-4799-a7fa-b2253df711b0)
![Screenshot from 2024-12-28 23-48-12](https://github.com/user-attachments/assets/90cbb719-9459-40a6-9819-b87452a15c14)



![Screenshot from 2024-12-28 23-48-42](https://github.com/user-attachments/assets/17596cad-1617-4170-9122-76b595fb58dc)


Usage
1.Deploy resources in the public and private VPCs.
2.Test connectivity between instances in both VPCs using tools like ping or telnet.
