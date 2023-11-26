<h1><b>TASK MANAGEMENT SYSTEM</b></h1>
<h3>Overview</h3>
<p>Task management system API allows Admins to create a new Task, assign tasks to users, update or delete those tasks.</p>
<h3>Getting Started</h3>
<p>To use the API, clone it from this repository.</p>
<p>In the command line, Run the following code:</p>

```
npm install
```
to run the code use:

```
node index.js
```
<h3>Usage</h3>
To use the API, first create a <b>.env</b> file with these values:

```
PORT = <Any port number>
MONGO_URI = <Your mongoDB connection string>
BCRYPT_SALT = 10
JWT_KEY = <Any String which will act as the key for JWT Authentication>
```

<h2>Admin</h2>
<p>This section is for creating and logging in as the admin, who has the power to create task, assign it to the users, update a task or even delete it. The admin can be anyone, like Team lead, Manager , etc.</p>

<h3>Register Admin</h3>

```
POST/admin/register
{
  "name": "Admin name",
  "email": "Email address",
  "password": "New password"
}
```
<h3>Login Admin</h3>

```
POST/admin/login
{
  "email": "Email address",
  "password": "Account password"
}
```

<h2>User</h2>
<p>This section is for creating and logging in as the user. They are the ones who gets assigned to a task by the admins.</p>
<h3>Register User</h3>

```
POST/user/register
{
  "name": "User name",
  "email": "Email address",
  "password": "New password"
}
```
<h3>Login User</h3>

```
POST/user/login
{
  "email": "Email address",
  "password": "Account password"
}
```

<h2>Tasks</h2>
<p>This section contains all endpoints for creating, updating, deleting and assigning users to a task. These can only be accessed by the admins.</p>
<p>In order to use these endpoints, one must login as admin to use them.</p>

<h3>Creating Task</h3>

```
POST/task/create
{
  "title" : "Task title",
  "description": "Task description",
  "due_date": "task due date",  // Type: Date
  "assigned_users": ["assigned user_id"],  //Array of strings containing user ids
}
```
<h3>Fetch all Tasks</h3>

```
GET/task/fetchAll
```

<h3>Fetch one Task</h3>

```
GET/task/fetch?task_id="enter_the_task_id_here"
```

<h3>Assign Task</h3>

```
POST/task/assign
{
  "task_id": "Task id",
  "user_id": "Assignee id"
}
```
<h3>Update Task</h3>
<p>To update a task, the task id is necessary, but everything else is optional </p>

```
PUT/task/update
{
  "task_id": "Task ID"
  "title" : "New Title"
  "description": "New description",
  "due_date": "New Due date",  //Type: Date
  "status": <status> //Type: Boolean (true => "Finished", false => "In progress")
}
```
<h3>Delete Task</h3>

```
DELETE/task/delete?task_id="task_id"
```
<h3>Analytics</h3>
<p>Fetches all the finished tasks in the last N days (where N is number of days)</p>

```
GET/task/analytics?days="no_of_days"
```







