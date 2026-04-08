# 🟢 Google Skills Lab - **Use Model Context Protocol (MCP) Tools with ADK Agents**    

* Lab - https://www.skills.google/paths/3273/course_templates/1275/labs/606599

<br> <br> 

---   

## 👉 Task 1. Install the ADK and set up your environment

```bash
git clone https://github.com/nov05/gcp-adk-mcp-tools.git
cd gcp-adk-mcp-tools
export PATH=$PATH:"/home/${USER}/.local/bin"
python3 -m pip install google-adk -r adk_mcp_tools/requirements.txt
```

<br>  

## 👉 Task 2. Use the Google Maps MCP server with ADK agents (ADK as an MCP client) in the ADK Dev UI

Get an API key and enable the APIs  

  * Go to the Google Cloud console browser tab (not your Cloud Shell Editor).     
    Search for `APIs` in the search bar at the top of the page. Select it from the results.   
    Go to `APIs & Services` → `Library`, try enabling: `Places API`, and click `+ Create Credential`.   
    For Name, type `GOOGLE_MAPS_API_KEY`. Click `Create`.      
    The API key created dialog displays your newly created API key.
    Be sure to copy and save this key locally for use later in the lab.   

<img src="https://raw.githubusercontent.com/nov05/pictures/refs/heads/master/gcp-adk-mcp-tools/2026-04-08%2003_19_11-NVIDIA%20GeForce%20Overlay.jpg" width=800>   
<img src="https://raw.githubusercontent.com/nov05/pictures/refs/heads/master/gcp-adk-mcp-tools/2026-04-08%2003_19_44-NVIDIA%20GeForce%20Overlay.jpg" width=800>     
 
```bash
export GOOGLE_MAPS_API_KEY=AIzaSyAOGDeMSVXFEYml9PCpWM4hpTTQvWveoo4  # ⚠️ Your own key
```
```bash
cd ~/gcp-adk-mcp-tools/adk_mcp_tools
cat << EOF > google_maps_mcp_agent/.env
GOOGLE_GENAI_USE_VERTEXAI=TRUE
# GOOGLE_CLOUD_PROJECT=qwiklabs-gcp-03-ade964eda587
GOOGLE_CLOUD_LOCATION=global
# GOOGLE_MAPS_API_KEY="YOUR_ACTUAL_API_KEY"
MODEL=gemini-3-flash-preview
EOF
cp google_maps_mcp_agent/.env adk_mcp_server/.env
```
```bash
cd ~/gcp-adk-mcp-tools/adk_mcp_tools
adk web --allow_origins "regex:https://.*\.cloudshell\.dev"
```

A new browser tab opens with the ADK Dev UI. From the Select an agent drop-down on the left, select the google_maps_mcp_agent.
Start a conversation with the agent and run the following prompts:  
```text
Get directions from GooglePlex to SFO.
```
```text    
What's the route from Paris, France to Berlin, Germany? 
```
```text
How do you get from Shanghai to Seattle?
```   

<img src="https://raw.githubusercontent.com/nov05/pictures/refs/heads/master/gcp-adk-mcp-tools/2026-04-08%2003_16_08-NVIDIA%20GeForce%20Overlay.jpg" width=800>    
<img src="https://raw.githubusercontent.com/nov05/pictures/refs/heads/master/gcp-adk-mcp-tools/2026-04-08%2003_36_54-NVIDIA%20GeForce%20Overlay.jpg" width=800>       

<br> 

## 👉 Task 3. Build an MCP server with ADK tools (MCP server exposing ADK)

```bash
python3 ~/gcp-adk-mcp-tools/adk_mcp_tools/adk_mcp_server/adk_server.py
```
In a new terminal window:  
```bash
export PATH_TO_YOUR_MCP_SERVER_SCRIPT="/home/$USER/gcp-adk-mcp-tools/adk_mcp_tools/adk_mcp_server/adk_server.py"
echo $PATH_TO_YOUR_MCP_SERVER_SCRIPT
cd ~/gcp-adk-mcp-tools/adk_mcp_tools
adk web --allow_origins "regex:https://.*\.cloudshell\.dev"
```

To view the web interface in a new tab, click the http://127.0.0.1:8000 link in the terminal output.  
From the Select an agent drop-down on the left, select the adk_mcp_server.    
Prompt the agent with the following:  
```text  
Load the content from http://example.com
```

<img src="https://raw.githubusercontent.com/nov05/pictures/refs/heads/master/gcp-adk-mcp-tools/2026-04-08%2002_47_22-NVIDIA%20GeForce%20Overlay.jpg" width=800>   





