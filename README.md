# just-a-bill-public
Serves as a description of the just-a-bill functionality
Try it [here](https://just-a-bill.netlify.app/)

What is the purpose of this site?
To provide users to insights on what their representatives are achieving in DC and utilize AI to explain bill texts in a comprehensive way

How does it work?
    Where does the data come from?
    The data is retrieved from the [congress.gov API](https://gpo.congress.gov/). This is an official API from the US government
    How does a user access the information?
    Originally, the user would ping the API anytime they wanted to pull data, this became taxing on the API rate limit of 5,000 requests per hour. Now they are accessing a local DB that is built into the code.
    
    How does the local DB update? Is the data fresh?
    
