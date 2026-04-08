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
```bash
export GOOGLE_MAPS_API_KEY=AIzaSyCF-dylB0OgG0UncAHkQIETpKczaVEqtjE  # ⚠️ Your own key
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
```
```bash
cp google_maps_mcp_agent/.env adk_mcp_server/.env
adk web --allow_origins "regex:https://.*\.cloudshell\.dev"
```

A new browser tab opens with the ADK Dev UI. From the Select an agent drop-down on the left, select the google_maps_mcp_agent.
Start a conversation with the agent and run the following prompts:  
`Get directions from GooglePlex to SFO.`    
`What's the route from Paris, France to Berlin, Germany?`   

<br> 

## 👉 Task 3. Build an MCP server with ADK tools (MCP server exposing ADK)

```bash
export PATH_TO_YOUR_MCP_SERVER_SCRIPT="/home/$USER/gcp-adk-mcp-tools/adk_mcp_tools/adk_mcp_server/adk_server.py"
echo $PATH_TO_YOUR_MCP_SERVER_SCRIPT
```
```bash
python3 ~/gcp-adk-mcp-tools/adk_mcp_tools/adk_mcp_server/adk_server.py
```





