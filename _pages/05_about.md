---
layout: page
title: About Us
permalink: /about/
---
This site is built by THE chris albertson
I am 16 years old and I really like fortnite and computer science

## Key Links
- GitHub Repos:  <a href="https://github.com/nighthawkcoders">github.com/nighthawkcoders</a>
- AWS Deployments: <a href="https://csa.nighthawkcodingsociety.com/">csp.nighthawkcodingsociety.com</a>
- - Slack: <a href="https://join.slack.com/t/cs-p-hq/shared_invite/zt-1ejp2nekj-vIeGHTAKR13E~648nh2NRg">Join Link</a>
- 2021-2022 Archives: <a href="https://padlet.com/jmortensen7/csp2022tri1">Fall</a>, <a href="https://padlet.com/jmortensen7/csp2022tri2">Early Winter</a>, <a href="https://cspcoders.nighthawkcodingsociety.com/">Late Winter, Spring</a>
![QR Code]({{site.baseurl}}/images/bit.ly_3T1z0jA.png)


<table>
  <thead>
  <tr>
    <th>Name</th>
    <th>ID</th>
  </tr>
  </thead>
  <tbody id="result">
    <!-- javascript generated data -->
  </tbody>
</table>

<script>
  // prepare HTML result container for new output
  const resultContainer = document.getElementById("result");

  // prepare fetch options
  const url = "https://csp.nighthawkcodingsociety.com/crud_api/read/";
  const options = {
    method: 'GET', // *GET, POST, PUT, DELETE, etc.
    mode: 'cors', // no-cors, *cors, same-origin
    cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
    credentials: 'omit', // include, *same-origin, omit
    headers: {
      'Content-Type': 'application/json'
      // 'Content-Type': 'application/x-www-form-urlencoded',
    },
  };

  // fetch the API
  fetch(url, options)
      // response is a RESTful "promise" on any successful fetch
    .then(response => {
      // check for response errors
      if (response.status !== 200) {
          const errorMsg = 'Database response error: ' + response.status;
          console.log(errorMsg);
          const tr = document.createElement("tr");
          const td = document.createElement("td");
          td.innerHTML = errorMsg;
          tr.appendChild(td);
          resultContainer.appendChild(tr);
          return;
      }
      // valid response will have json data
      response.json().then(data => {
          console.log(data);
          for (let row in data) {
            // tr and td build out for each row
            const tr = document.createElement("tr");
            const name = document.createElement("td");
            const id = document.createElement("td");
            // data is specific to the API
            name.innerHTML = data[row].name; 
            id.innerHTML = data[row].email; 
            // add HTML to container
            tr.appendChild(name);
            tr.appendChild(id);
            resultContainer.appendChild(tr);
          }
      })
  })
  // catch fetch errors (ie ACCESS to server blocked)
  .catch(err => {
    console.error(err);
    const tr = document.createElement("tr");
    const td = document.createElement("td");
    td.innerHTML = err;
    tr.appendChild(td);
    resultContainer.appendChild(tr);
  });
</script>
