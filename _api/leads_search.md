---
title: Search Leads
position_number: 1.2
type: get
description: This endpoint allows you to search for leads in the Slintel Database.
parameters:
  - name: titles
    content: titles (eg. cxo, manager, vp)
  - name: company_websites
    content: domain of the company
  - name: location
    content: location of leads
  - name: page
    content: page number to extract the records
content_markdown: |-
  Returns a matched company from Slintel database.
  
  This call will return a maximum of 50 leads
  {: .info }
left_code_blocks:
  - code_block: |-
        var request = require('request');
        var options = {
          'method': 'POST',
          'url': 'https://apiv2.slintel.com/v2.0/lead/search',
          'headers': {
            'x-api-key': 'YOUR API KEY',
            'Content-Type': 'application/json'
          },
          body: JSON.stringify({"payload":{"titles":["cxo","vp"],"company_websites":["amazon.com"],"location":["california","united stated"]},"page":1})
        };
        request(options, function (error, response) { 
          if (error) throw new Error(error);
          console.log(response.body);
        });

    title: Nodejs
    language: javascript
  - code_block: |-
        var settings = {
          "url": "https://apiv2.slintel.com/v2.0/lead/search",
          "method": "POST",
          "timeout": 0,
          "headers": {
            "x-api-key": "YOUR API KEY",
            "Content-Type": "application/json"
          },
          "data": JSON.stringify({"payload":{"titles":["cxo","vp"],"company_websites":["amazon.com"],"location":["california","united stated"]},"page":1}),
        };
        
        $.ajax(settings).done(function (response) {
          console.log(response);
        });
    title: jQuery
    language: javascript
  - code_block: |-
        import requests

        url = "https://apiv2.slintel.com/v2.0/lead/search"
        
        payload = "{\"payload\":{\"titles\":[\"cxo\",\"vp\"],\"company_websites\":[\"amazon.com\"],\"location\":[\"california\",\"united stated\"]},\"page\":1}"
        headers = {
          'x-api-key': 'YOUR API KEY',
          'Content-Type': 'application/json'
        }
        
        response = requests.request("POST", url, headers=headers, data = payload)
        
        print(response.text.encode('utf8'))
    title: Python
    language: python
right_code_blocks:
  - code_block: |2-
        {
          "payload": {
            "titles": [
              "cxo",
              "vp"
            ],
            "company_websites": [
              "amazon.com"
            ],
            "location": [
              "california",
              "united stated"
            ]
          },
          "page": 1
        }
    title: Request
    language: json
  - code_block: |2-
        {
            "data": [
            {
                "id": "607f5251efe2c7542c97661f",
                "company_id": "5c3b000ad55ae49f1b75f1a3",
                "email_confidence": "High",
                "lead_title": "Vice President Ad Sales And Program Management",
                "company_name": "Amazon",
                "company_website": "amazon.com",
                "name": "Steve Sarner",
                "linkedin_url": "http://www.linkedin.com/in/stevesarner",
                "email": "s*****r@amazon.com"
            }
        ],
        "total": 442
        }
    title: Response
    language: json
---