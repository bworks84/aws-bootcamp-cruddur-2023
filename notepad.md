# Database instructions

- pool-1 error -> ./bin/db/drop manually

- if too many connections error:
    - REVOKE CONNECT ON DATABASE cruddur FROM public;
    - ALTER DATABASE cruddur allow_connections = off;
    - SELECT pg_terminate_backend(pg_stat_activity.pid) FROM pg_stat_activity WHERE pg_stat_activity.datname = 'cruddur';
    - DROP DATABASE cruddur;
    - \q out of db
    -./bin/db/drop
    -./bin/db/setup
    -./bin/db/connect to verify (select * from users;)

- ./bin/ddb/schema-load
- ./bin/ddb/seed
- ./bin/ddb/scan
- ./bin/ddb/patterns/list-conversations
- ./bin/ddb/patterns/get-conversations

"Should work now for messages"

aws ecs execute-command  \
--region $AWS_DEFAULT_REGION \
--cluster cruddur \
--task 8f07a543460f4bd9b69de01abd9c0be6 \
--container backend-flask \
--command "/bin/bash" \
--interactive


