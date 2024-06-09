# REST API endpoints for examinations
<procedure>
<p>Use <code>examinations</code> endpoints for creating, modifying, deleting examinations and
updating an examination's status.</p>
</procedure>

> Unless otherwise stated, all endpoints listed here requires
> authenticating with a session token. Authenticating anonymously
> or with login-password will generally result in a `403 Forbidden`
> error. See more about authentication.

## List examinations

<tldr><p><code lang="http">GET /v1/examinations</code></p>
<p>Lists all examination objects.</p></tldr>

<note>While populating all examinations is allowed, 
it is suggested to use pagination to get examinations chunk by chunk to avoid
causing stress to the server.</note>

### Request parameters {id="request_params_0"}

#### Query parameters {id="query_params_0"}

<deflist>

<def>
<title><code>page</code>:<code>integer</code></title>
<p>The page number of results to fetch.</p>
<p>Default: <code>1</code></p>
</def>

<def>
<title><code>per_page</code>:<code>integer</code></title>
<p>The number of results per page. Set to <code>0</code> for populating all results.</p>
<p>Default: <code>30</code></p>
</def>

</deflist>

### Responses {id="responses_0"}

<procedure collapsible="true">
<title><code>200 OK</code></title>

<p>The request was successful. Example response:</p>

```json
[
  {
    "examination_id": 234829,
    "examination_name": "23/24 S.4 Term 2 Exam (English Language II)",
    "examination_year": "23/24",
    "examination_level": "S4E2",
    "subject_code": "A020E",
    "subject_name": "English Language",
    "paper_code": "002",
    "paper_name": "Paper II - Writing"
  },
  {
    "examination_id": 234839,
    "examination_name": "23/24 S.4 Term 2 Exam (Maths Extended 2)",
    "examination_year": "23/24",
    "examination_level": "S4E2",
    "subject_code": "A032E",
    "subject_name": "Mathematics Extended Module 2",
    "paper_code": "001",
    "paper_name": "Paper I - Algebra & Calculus"
  }
]
```
</procedure>

<procedure collapsible="true">
<title><code>403 Forbidden</code></title>

<p>The request is forbidden under the current authorisation credentials.</p>
</procedure>


## Get an examination

<tldr><code>GET /v1/examinations/{exam_id}</code>
<p>Gets an examination with the specified ID.</p></tldr>

### Request parameters {id="request_params_1"}

#### Path parameters {id="path_params_1"}

<deflist>

<def>
<title><code>exam_id</code>:<code>integer</code> (<b>required</b>)</title>
<p>The ID of the examination to retrieve.</p>
</def>

</deflist>

### Responses {id="responses_1"}

<procedure collapsible="true">
<title><code>200 OK</code></title>

Example response:

```json
{
  "examination_id": 234839,
  "examination_name": "23/24 S.4 Term 2 Exam (Maths Extended 2)",
  "examination_year": "23/24",
  "examination_level": "S4E2",
  "subject_code": "A032E",
  "subject_name": "Mathematics Extended Module 2",
  "paper_code": "001",
  "paper_name": "Paper I - Algebra & Calculus"
}
```

</procedure>

<procedure collapsible="true">
<title><code>403 Forbidden</code></title>

<p>The request is forbidden under the current authorisation credentials.</p>
</procedure>

<procedure collapsible="true">
<title><code>404 Not Found</code></title>

The requested resource could not be found.
</procedure>