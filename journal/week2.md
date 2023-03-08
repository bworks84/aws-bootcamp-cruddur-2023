# Week 2 — Distributed Tracing

## AWS and Honeycomb Observability Services
- AWS CloudWatch Logs, CloudWatch Metrics, and X-Ray Traces
- Monitoring vs Observability: 
    - Monitoring - measures the health of an application. Helps teams watch system performance and detect known failures. 
    - Observability - the ability to understand a complex system's internal states based on external outputs. 
        - 3 pillars are metrics, traces, and logs

## Honeycomb.io
First instructional this week was installing honeycomb's observability tool, specifically the distributed tracing, to our Cruddur app to help debug  
    
## X-Ray
Set up AWS X-Ray on useractivities for backend and tested in AWS dashboard.  Still need to attempt setting up xray between the frontend/backend. 
 - Added subsegments after watching tutorial, verified app and X-ray traces were logging in AWS dashboard

## CloudWatch
Set up AWS CloudWatch on homeactivities in backend, tested in AWS dashboard. Required a bit of debugging to get input parameters correct between homeactivities run function and app.py data_home func. 

## Watched: 


#### To Do :
    - Research all three services
    - Finish Codespaces tutorial.  Stopped until I get closer to using all gitpod hours