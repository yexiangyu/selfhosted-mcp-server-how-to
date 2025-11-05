# selfhosted-mcp-server-how-to

1. Install `supabase` by docker:

https://supabase.com/docs/guides/self-hosting/docker

2. expose postgresql port 5432 of `db` in `supabase`'s `docker-compose.yml` file:

![alt text](image.png)

3. Install mcp server

https://github.com/HenkDz/selfhosted-supabase-mcp

4. create `mcpServers` in agent configuration: 

```json
{
  "mcpServers": {
    "selfhosted-supabase": {
      "command": "node",
      "args": [
        "/Users/yexiangyu/Repo/dev-tools/selfhosted-supabase-mcp/dist/index.js",
        "--url",
        "http://localhost:8000",
        "--anon-key",
        "you-anon-key",
        "--service-key",
        "you-service-role-key",
        "--db-url",
        "postgresql://postgres:your-super-secret-and-long-postgres-password@localhost:5433/postgres",
        "--jwt-secret",
        "your-super-secret-jwt-token-with-at-least-32-characters-long"
      ]
    }
  }
}
```
