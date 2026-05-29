<img width="1440" height="740" alt="Screenshot 2026-05-28 at 5 08 42 PM" src="https://github.com/user-attachments/assets/08b9f46f-7711-4571-9f3b-acd61d61c7e5" />

<img width="1440" height="740" alt="Screenshot 2026-05-28 at 5 09 05 PM" src="https://github.com/user-attachments/assets/92e82606-d022-4eae-9cbb-b4be12bee6ce" />

<img width="1440" height="740" alt="Screenshot 2026-05-28 at 5 10 25 PM" src="https://github.com/user-attachments/assets/b6db3e85-ea7b-45a2-9585-3b9fb4b66adf" />

<img width="1440" height="740" alt="Screenshot 2026-05-28 at 5 13 45 PM" src="https://github.com/user-attachments/assets/1706d364-f5d2-45ca-b5d1-2578c1570f26" />

<img width="1440" height="740" alt="Screenshot 2026-05-28 at 5 14 24 PM" src="https://github.com/user-attachments/assets/359a0ca3-10d1-4e46-a9ea-23ec26f2abb3" />

<img width="1440" height="740" alt="Screenshot 2026-05-28 at 5 24 23 PM" src="https://github.com/user-attachments/assets/f7f97683-09f4-4e98-af05-49546552c423" />

<img width="1440" height="740" alt="Screenshot 2026-05-28 at 5 25 12 PM" src="https://github.com/user-attachments/assets/8f7f73dd-5303-442e-abc5-1017e800ab3d" />

<img width="1440" height="740" alt="Screenshot 2026-05-28 at 5 33 00 PM" src="https://github.com/user-attachments/assets/5a5a8296-7103-489d-a82a-2afea771d469" />

<img width="1440" height="740" alt="Screenshot 2026-05-28 at 5 33 08 PM" src="https://github.com/user-attachments/assets/7f8d0ffb-342e-485e-ba93-e85407e053ef" />

<img width="1440" height="740" alt="Screenshot 2026-05-28 at 8 23 42 PM" src="https://github.com/user-attachments/assets/76e84cc0-e56b-4b28-88a1-c4d0278c2e84" />

<img width="1440" height="740" alt="Screenshot 2026-05-28 at 8 24 10 PM" src="https://github.com/user-attachments/assets/2eb8b805-4753-41ce-ae2a-9fb0a7914f06" />

<img width="1440" height="740" alt="Screenshot 2026-05-28 at 8 24 31 PM" src="https://github.com/user-attachments/assets/f71eb69e-c0b6-4bab-aa90-5c90fd24e71c" />

<img width="1440" height="740" alt="Screenshot 2026-05-29 at 1 45 59 PM" src="https://github.com/user-attachments/assets/848dc1d2-03bb-471d-8d63-41320a0d8c88" />

<img width="1440" height="740" alt="Screenshot 2026-05-29 at 1 48 51 PM" src="https://github.com/user-attachments/assets/d9ef7c5d-02ab-485d-860f-544afcc79251" />

<img width="1440" height="740" alt="Screenshot 2026-05-29 at 1 49 01 PM" src="https://github.com/user-attachments/assets/45bacf6a-423e-4f28-8e77-3d0bc449358f" />

<img width="1440" height="740" alt="Screenshot 2026-05-29 at 1 49 44 PM" src="https://github.com/user-attachments/assets/a36104ec-07a9-42a3-871b-635979072f59" />

<img width="1440" height="740" alt="Screenshot 2026-05-29 at 1 51 57 PM" src="https://github.com/user-attachments/assets/d3a767ff-9560-4b7b-8c25-ecb3ba7faec7" />

<img width="1440" height="740" alt="Screenshot 2026-05-29 at 1 53 25 PM" src="https://github.com/user-attachments/assets/f5636f4f-e486-4f24-b653-710300a09ff2" />

<img width="1440" height="740" alt="Screenshot 2026-05-29 at 1 54 51 PM" src="https://github.com/user-attachments/assets/ba777263-0f46-49e5-854f-053f28de7673" />

<img width="1440" height="740" alt="Screenshot 2026-05-29 at 1 55 30 PM" src="https://github.com/user-attachments/assets/0077f521-1f94-4750-a653-a6e5d78df0db" />

ACRNAME=$(az acr list --resource-group AZ500LAB09 --query '[].{Name:name}' --output tsv)

az aks update -n MyKubernetesCluster -g AZ500LAB09 --attach-acr $ACRNAME


<img width="1440" height="740" alt="Screenshot 2026-05-29 at 1 56 48 PM" src="https://github.com/user-attachments/assets/b8c368e2-6860-4914-bb0a-7d006d70fffb" />

RG_AKS=AZ500LAB09

RG_VNET=MC_AZ500LAB09_MyKubernetesCluster_eastus    

AKS_VNET_NAME=aks-vnet-30198516

AKS_CLUSTER_NAME=MyKubernetesCluster

AKS_VNET_ID=$(az network vnet show --name $AKS_VNET_NAME --resource-group $RG_VNET --query id -o tsv)

AKS_MANAGED_ID=$(az aks show --name $AKS_CLUSTER_NAME --resource-group $RG_AKS --query identity.principalId -o tsv)

az role assignment create --assignee $AKS_MANAGED_ID --role "Contributor" --scope $AKS_VNET_ID

<img width="1440" height="740" alt="Screenshot 2026-05-29 at 2 00 05 PM" src="https://github.com/user-attachments/assets/58212c63-c7e2-40a2-a667-0cb86fee50f9" />



