# Redis Cheat Sheet

This cheat sheet provides an overview of the most commonly used Redis commands, with short explanations to help you quickly understand their functionality.

## Table of Contents

1. [Keys](#keys)
2. [Strings](#strings)
3. [Hashes](#hashes)
4. [Lists](#lists)
5. [Sets](#sets)
6. [Sorted Sets (ZSets)](#sorted-sets-zsets)
7. [Pub/Sub](#pubsub)
8. [Transactions](#transactions)
9. [Scripting](#scripting)
10. [Server Management](#server-management)

## Key Commands
- **`DEL key`**: Delete a key.
- **`DUMP key`**: Serialize the value stored at key.
- **`EXISTS key`**: Check if a key exists.
- **`EXPIRE key seconds`**: Set a timeout on a key.
- **`EXPIREAT key timestamp`**: Set the expiration for a key as a UNIX timestamp.
- **`KEYS pattern`**: Find all keys matching the pattern.
- **`PERSIST key`**: Remove the expiration from a key.
- **`PEXPIRE key milliseconds`**: Set a timeout on a key in milliseconds.
- **`PEXPIREAT key milliseconds-timestamp`**: Set the expiration for a key as a UNIX timestamp in milliseconds.
- **`TTL key`**: Get the remaining time to live of a key.
- **`PTTL key`**: Get the remaining time to live of a key in milliseconds.
- **`RENAME key newkey`**: Rename a key.
- **`RENAMENX key newkey`**: Rename a key, only if the new key does not exist.
- **`TYPE key`**: Determine the type of the value stored at key.

## String Commands
- **`SET key value`**: Set the string value of a key.
- **`GET key`**: Get the value of a key.
- **`SETNX key value`**: Set the value of a key if it does not already exist.
- **`SETEX key seconds value`**: Set the value of a key with an expiration.
- **`MSET key value [key value ...]`**: Set multiple keys to multiple values.
- **`MGET key [key ...]`**: Get the values of multiple keys.
- **`INCR key`**: Increment the integer value of a key by one.
- **`DECR key`**: Decrement the integer value of a key by one.
- **`INCRBY key increment`**: Increment the integer value of a key by a given amount.
- **`DECRBY key decrement`**: Decrement the integer value of a key by a given amount.
- **`APPEND key value`**: Append a value to a key.
- **`STRLEN key`**: Get the length of the value stored in a key.

## Hash Commands
- **`HSET key field value`**: Set the hash field to the specified value.
- **`HGET key field`**: Get the value of a hash field.
- **`HDEL key field [field ...]`**: Delete one or more hash fields.
- **`HLEN key`**: Get the number of fields in a hash.
- **`HKEYS key`**: Get all the fields in a hash.
- **`HVALS key`**: Get all the values in a hash.
- **`HGETALL key`**: Get all the fields and values in a hash.
- **`HINCRBY key field increment`**: Increment the integer value of a hash field by a given amount.
- **`HSETNX key field value`**: Set the hash field to the specified value only if the field does not already exist.

## List Commands
- **`LPUSH key value [value ...]`**: Prepend one or multiple values to a list.
- **`RPUSH key value [value ...]`**: Append one or multiple values to a list.
- **`LPOP key`**: Remove and get the first element of a list.
- **`RPOP key`**: Remove and get the last element of a list.
- **`LRANGE key start stop`**: Get a range of elements from a list.
- **`LLEN key`**: Get the length of a list.
- **`LRPUSH key value`**: Append a value to the end of a list.
- **`LREM key count value`**: Remove the first count occurrences of elements equal to value from the list.
- **`LSET key index value`**: Set the value of an element in a list by its index.
- **`LINSERT key before|after pivot value`**: Insert an element before or after another element in a list.

## Set Commands
- **`SADD key member [member ...]`**: Add one or more members to a set.
- **`SREM key member [member ...]`**: Remove one or more members from a set.
- **`SMEMBERS key`**: Get all the members in a set.
- **`SISMEMBER key member`**: Check if a member exists in a set.
- **`SCARD key`**: Get the number of members in a set.
- **`SPOP key`**: Remove and return a random member from a set.
- **`SRANDMEMBER key [count]`**: Get one or more random members from a set.
- **`SDIFF key [key ...]`**: Get the difference between two or more sets.
- **`SDIFFSTORE destination key [key ...]`**: Store the difference between two or more sets in a key.
- **`SINTER key [key ...]`**: Get the intersection of two or more sets.
- **`SINTERSTORE destination key [key ...]`**: Store the intersection of two or more sets in a key.
- **`SUNION key [key ...]`**: Get the union of two or more sets.
- **`SUNIONSTORE destination key [key ...]`**: Store the union of two or more sets in a key.

## Sorted Set Commands
- **`ZADD key score member [score member ...]`**: Add one or more members to a sorted set, or update the score of an existing member.
- **`ZREM key member [member ...]`**: Remove one or more members from a sorted set.
- **`ZRANGE key start stop [WITHSCORES]`**: Return a range of members in a sorted set, by index.
- **`ZREVRANGE key start stop [WITHSCORES]`**: Return a range of members in a sorted set, by index, in descending order.
- **`ZRANGEBYSCORE key min max [WITHSCORES] [LIMIT offset count]`**: Return all the members in a sorted set with a score between min and max.
- **`ZREVRANGEBYSCORE key max min [WITHSCORES] [LIMIT offset count]`**: Return all the members in a sorted set with a score between max and min, in descending order.
- **`ZCARD key`**: Get the number of members in a sorted set.
- **`ZINCRBY key increment member`**: Increment the score of a member in a sorted set.
- **`ZSCORE key member`**: Get the score associated with the member in a sorted set.
- **`ZCOUNT key min max`**: Count the members in a sorted set with scores within the given values.
- **`ZPOPMIN key [count]`**: Remove and return the member(s) with the lowest score in a sorted set.
- **`ZPOPMAX key [count]`**: Remove and return the member(s) with the highest score in a sorted set.

## HyperLogLog Commands
- **`PFADD key element [element ...]`**: Add elements to the HyperLogLog data structure.
- **`PFCOUNT key [key ...]`**: Get the approximated cardinality of the HyperLogLog.
- **`PFMERGE destkey sourcekey [sourcekey ...]`**: Merge multiple HyperLogLogs into a single one.

## Pub/Sub Commands
- **`PUBLISH channel message`**: Post a message to a channel.
- **`SUBSCRIBE channel [channel ...]`**: Subscribe to one or more channels.
- **`UNSUBSCRIBE [channel [channel ...]]`**: Unsubscribe from one or more channels, or all channels.
- **`PSUBSCRIBE pattern [pattern ...]`**: Subscribe to channels matching the given patterns.
- **`PUNSUBSCRIBE [pattern [pattern ...]]`**: Unsubscribe from channels matching the given patterns, or all patterns.

## Transaction Commands
- **`MULTI`**: Start a transaction.
- **`EXEC`**: Execute all commands issued after MULTI.
- **`DISCARD`**: Discard all commands issued after MULTI.
- **`WATCH key [key ...]`**: Watch one or more keys for changes.

## Scripting Commands
- **`EVAL script numkeys key [key ...] arg [arg ...]`**: Execute a Lua script.
- **`EVALSHA sha1 numkeys key [key ...] arg [arg ...]`**: Execute a Lua script using its SHA1 hash.
- **`SCRIPT LOAD script`**: Load a script into the script cache.
- **`SCRIPT EXISTS sha1 [sha1 ...]`**: Check existence of scripts in the script cache.
- **`SCRIPT FLUSH`**: Remove all the scripts from the script cache.
- **`SCRIPT KILL`**: Kill the currently executing script.

## Server Commands
- **`INFO [section]`**: Get information and statistics about the server. Sections include `server`, `clients`, `memory`, `persistence`, `stats`, `replication`, `cpu`, `commandstats`, `cluster`, `keyspace`, etc.
- **`CONFIG GET parameter`**: Get the value of a configuration parameter.
- **`CONFIG SET parameter value`**: Set the value of a configuration parameter.
- **`CONFIG RESETSTAT`**: Reset the stats returned by INFO.
- **`SHUTDOWN [nosave|save]`**: Shut down the Redis server. `nosave` skips saving the data to disk, while `save` saves the data before shutting down.
- **`SAVE`**: Save the dataset to disk (synchronous).
- **`BGSAVE`**: Save the dataset to disk asynchronously (background save).
- **`BGREWRITEAOF`**: Rewrite the append-only file (AOF) in the background.
- **`LASTSAVE`**: Get the UNIX timestamp of the last successful save to disk.
- **`MONITOR`**: Monitor the commands processed by the Redis server in real time.
- **`SLAVEOF host port`**: Make the server a slave of another server (used for replication). Use `SLAVEOF NO ONE` to make it a master.
- **`REPLICAOF host port`**: Similar to `SLAVEOF`, used in Redis 5.0+.
- **`ROLE`**: Get the role of the server (master or slave).
- **`DEBUG OBJECT key`**: Get debugging information about a key.
- **`DEBUG SEGFAULT`**: Make the server crash for debugging purposes.
- **`CLUSTER INFO`**: Get cluster information (for Redis Cluster setups).
- **`CLUSTER NODES`**: List all nodes in the cluster.
- **`CLUSTER MEET ip port`**: Force a node to join the cluster.
- **`CLUSTER FORGET node_id`**: Forget a node in the cluster.
- **`CLUSTER REPLICATE node_id`**: Make the current node a replica of the specified node.
- **`CLUSTER RESET [HARD|SOFT]`**: Reset the cluster state.
- **`CLIENT LIST`**: Get a list of connected clients.
- **`CLIENT KILL [ID client-id | TYPE type | addr host:port | ...]`**: Kill a client connection.
- **`CLIENT GETNAME`**: Get the name of the current connection.
- **`CLIENT SETNAME connection-name`**: Set the name of the current connection.
- **`LATENCY DOCTOR`**: Provide a diagnostic report on latency issues.
- **`LATENCY HISTORY command`**: Get latency history for a specific command.
- **`LATENCY LATEST`**: Get the latest latency data.
- **`LATENCY MONITOR`**: Enable or disable latency monitoring.

## Keyspace Notifications
- **`CONFIG SET notify-keyspace-events events`**: Enable or disable keyspace notifications. `events` can be a combination of `K` (Keyspace), `E` (Keyevent), and `g` (generic events).

## Sentinel Commands (for Redis Sentinel setups)
- **`SENTINEL MONITOR name ip port quorum`**: Monitor a Redis master.
- **`SENTINEL SLAVES name`**: List all slaves of the given master.
- **`SENTINEL SENTINELS name`**: List all sentinels monitoring the given master.
- **`SENTINEL REMOVE name`**: Remove a monitored master from the Sentinel configuration.
- **`SENTINEL RESET pattern`**: Reset the state of Sentinel for a given pattern.
- **`SENTINEL FAILOVER name`**: Trigger a failover of the monitored master.

## Cluster Commands
- **`CLUSTER MEET ip port`**: Join the cluster with the given node.
- **`CLUSTER LEAVE`**: Remove the node from the cluster.
- **`CLUSTER FORGET node_id`**: Remove a node from the cluster.
- **`CLUSTER REPLICATE node_id`**: Make the current node a replica of the specified node.
- **`CLUSTER RESET [HARD|SOFT]`**: Reset the cluster state.

This cheatsheet covers a comprehensive list of Redis commands. For more detailed information or additional commands, refer to the [official Redis documentation](https://redis.io/commands).
