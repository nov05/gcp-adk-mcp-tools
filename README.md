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

### Get an API key and enable the APIs  

In this sub-section, you generate a new API key named GOOGLE_MAPS_API_KEY.

Go to the Google Cloud console browser tab (not your Cloud Shell Editor).

You can close the Cloud Shell terminal pane in this browser tab for more console area.

Search for Credentials in the search bar at the top of the page. Select it from the results.

On the Credentials page, click Create credentials at the top of the page, then select API key.

For Name, type GOOGLE_MAPS_API_KEY. Click Create.

The API key created dialog displays your newly created API key. Be sure to copy and save this key locally for use later in the lab.

Click Close on the dialog box.

<br> 

## 👉 Task 3. Build an MCP server with ADK tools (MCP server exposing ADK)
