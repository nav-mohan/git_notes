<h1> Github Actions and Branch Status Checks </h1>

<h2> Github Actions </h2>

<li> The workflow configurations are located inside the <code>./github/workflows</code> directory. Currently it contains just one workflow <code>end-to-end-tests.yml</code></li>


<code>

    name: End-to-end tests                      
    
    on:
    pull_request:                               # WORKFLOW TRIGGER
        branches:   
        - "master"  
        - "dev"     
    
    jobs:
      cypress-run:                              # NAME OF THE JOB
        runs-on: ubuntu-latest                  # SERVER VERSION
        steps:
          - name: Checkout                      # CHECKOUT THE CODE
            uses: actions/checkout@v2

          - name: Cypress run             
            uses: cypress-io/github-action@v4   # TEMPLATE cypress-io/github-action@v4
            with:
              start: npm run test               # DEPLOY THE NODE SERVER

</code>

<li> At the moment, the workflow contains only 1 job called <code>cypress-run</code>. 
<li> It consists of two steps 
    <ol>
        <li> Checkout the code. This is usually the first step for most Github Actions. 
        <li> Execute the Cypress tests with the Node server running in <code> test </code> configuration
    </ol>
</li>
<li> Both of these steps use specific <code> Github Action Templates </code>. A template is essentially a wrapper around some <code>shell scripts</code>.</li> 
<li> The template <code>actions/checkout@v2</code> moves all of our code into a virtual environment on the Ubuntu server in preparation for the next step. </li>
<li> The template Github Action <code>cypress-io/github-action@v4</code> then installs all the NPM dependencies (<code> npm install </code>) and executes the Cypress tests ( <code> npx cypress run </code>) </li>
<li> Now, when we make a pull-request we can verify that our workflow has been incorporated by going to the <code> Actions </code> tab in the repository. </li>



<br>
<br>
<h2> Enabling <a href = "https://help.github.com/en/github/administering-a-repository/enabling-required-status-checks">Status Checks</a>  </h2>
<li> First make a pull-request to the master branch or dev branch and verify that our <code>end-to-end-tests.yml</code> workflow has been confiured correctly. 
<li> After verifying that our <code>end-to-end-tests.yml</code> has been configured correctly we can now use this workflow as a <code>status-check</code> to protect our branches. 
<li> To protect the <code>master</code> branch with this workflow: 
<ol>
    <li>go to <code>Settings</code> --> <code>Branches</code> --> <code>Add Rule </code></ul>
    <li>Use <code>"master"</code> for the <code>Branch name pattern</code></ul>
    <li>Check the option <code> Require status checks to pass before merging </code></ul>
    <li>In the search bar, type in the name of the job. Which in this case was "<code>cypress-run</code>". Its not "<code>End-to-end tests</code>"!
</li>
</ol>