<h1>Database Schema (NoSql)</h1>

<h2>Collections:</h2>

<h3>User:</h3>
<p>Fields: nickname, password</p>

<h3>SleepAssessments:</h3>
<p>Fields: AssessmentId, UserId, Questions (Array of Objects), Date</p>

<h3>Packs:</h3>
<p>Fields: PackId, Name, Description, Techniques (Array of Objects)</p>
<p>Each technique object includes:</p>
<ul>
  <li>Name: Name of the technique.</li>
  <li>Description: Description of the technique.</li>
  <li>Exercise: Exercise details.</li>
</ul>

<h1>REST API flow:</h1>

<h3>Sleep Assessment Submission:</h3>
<p><b>Endpoint:</b> /api/users/:userId/sleep-assessment</p>
<p><b>Request:</b></p>
<ul>
  <li>Method: POST</li>
  <li>Body:</li>
</ul>
<pre>
        <code>
{
  "questions": [
    {
      "question": "What do you want to improve?",
      "answers": ["I want to sleep easily", "I want to sleep better"]
    },
    // Additional questions...
  ]
}
        </code>
    </pre>
<p><b>Response:</b></p>
<ul>
  <li>Status: 200 OK</li>
  <li>Body: { "assessmentId": "789012" }</li>
</ul>

<h3>Retrieve Sleep Assessment:</h3>
<p><b>Endpoint:</b> /api/users/:userId/sleep-assessment/:assessmentId</p>
<p><b>Request:</b></p>
<ul>
  <li>Method: GET</li>
</ul>
<p><b>Response:</b></p>
<ul>
  <li>Status: 200 OK</li>
</ul>
<pre>
        <code>
{
  "assessmentId": "789012",
  "questions": [
    {
      "question": "What do you want to improve?",
      "answers": ["I want to sleep easily", "I want to sleep better"]
    },
    // Additional questions...
  ]
}
        </code>
    </pre>

<h3>Calculate Sleep Efficiency:</h3>
<p>
  <b>Endpoint:</b>
  /api/users/:userId/sleep-assessment/:assessmentId/sleep-efficiency
</p>
<p><b>Request:</b></p>
<ul>
  <li>Method: GET</li>
</ul>
<p><b>Response:</b></p>
<ul>
  <li>Status: 200 OK</li>
</ul>
<p>Body: { "sleepEfficiencyPercentage": 85 }</p>

<h3>Get All Packs:</h3>
<p>
  <b>Endpoint:</b>
  /api/users/:userId/sleep-assessment/:assessmentId/all-packs
</p>
<p><b>Request:</b></p>
<ul>
  <li>Method: GET</li>
</ul>
<p><b>Response:</b></p>
<ul>
  <li>Status: 200 OK</li>
  <li>Body:</li>
</ul>
<pre>
        <code>
{
  "packs": [
    {
      "packId": "1",
      "name": "Relaxation Techniques",
      "description": "Techniques to promote relaxation and better sleep.",
      "techniques": [
        {
          "name": "Deep Breathing",
          "description": "Practice deep breathing for relaxation.",
          "exercise": "Inhale for 4 seconds, hold for 4 seconds, exhale for 4 seconds. Repeat."
        },
        // Additional techniques...
      ]
    },
    // Additional packs...
  ]
}
        </code>
    </pre>
