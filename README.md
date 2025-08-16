# Sinks-and-Sources

In this post, I break down how to identify **sinks** and **sources** during a source code review — a critical skill in offensive security and secure code analysis.

## Key Concepts

- **Sources**: Where user input enters the application.
- **Sinks**: Where that input is used in a potentially dangerous way (e.g., SQL queries, system calls).

## Techniques

- Use static analysis tools like Semgrep or CodeQL.
- Manually trace input flow from source to sink.
- Flag functions like `eval()`, `exec()`, `system()`, and database queries.

## Example
python code vulnerable to SQL injection
```
user_input = request.GET['name']
query = "SELECT * FROM users WHERE name = '" + user_input + "'"
cursor.execute(query)
```

solution using a parametized query
```
user_input = request.GET['name']
query = "SELECT * FROM users WHERE name = %s"
cursor.execute(query, (user_input,))

```
## Meduim Blog
You can read the full article on [Medium](https://medium.com/@prudiee/source-code-review-identifying-sinks-and-sources-15c94fb0d253).
