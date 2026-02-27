# COMP-304-Shell-ish-Spring-2026-Assignment-1-Ozan Ozak (oozak23)
First assignment of COMP 304 Course

## To build and run:

```bash
gcc -o shell-ish shellish-skeleton.c
./shell-ish
```

## Part 1: Basic Command Execution:

* In this part I've executed standard commands such as ls, mkdir etc.
* Background execution is also supported by adding `&`  to any command
 ```bash
sleep 10 &
```
  
## Part 2: I/O Redirection and Piping:

1) Output Redirection: Creates or truncates the file

```bash
ls -la >output.txt
```

2) Append redirection : creates or appends to the file
```bash
echo "hello" >>log.txt
```

3) Input Redirection: Reads from the file

```bash
cut -d : -f1 <input.txt
```

4) Piping: handled recursively and used between commands with `|`

```bash
ls -la | grep shell | wc -l
```

### Part 3: Creating Commands

1) `cut` Command:

* I implemented the Unix `cut` command. This command reads the lines from stdin and prints only the wanted fields. There are multiple options to use these command such as:

  1) `-d` / `--delimiter` — specify a delimiter
  2) -f` / `--fields` — comma-separated list of field to print
 
```bash
cat /etc/passwd | cut -d: -f1,6
echo "a,b,c,d" | cut -d, -f2,4
```

2) `chatroom` Command:

* Chatroom command is used for letting users chat with eac other. Each user gets a named pipe inside a shared folder.

**Usage:**
```bash
chatroom  
```

**Example:**
```bash
chatroom comp304 alice   # Terminal 1
chatroom comp304 bob     # Terminal 2
```

* If the room does not exist it is created at `/tmp/chatroom-<roomname>/`
* If the user doesn't exist in the room, a named pipe is created for them
* Messages typed by one user appear in all other users' terminals
* User can exit the terminal by typing `exit` or pressing `Ctrl + D`. Pipe is removed when the user exits

3) `remindme` - Custom Command:

* A timed reminder can be seen in users terminal after the specified number of seconds is passed.
* User chooses the number of seconds and the message he/she wants to see.

**Usage:**
```bash
remindme  
```

**Examples:**
```bash
remindme 10 check the oven
remindme 60 take a break
remindme 300 meeting starts soon
```

After the specified time, the shell prints:
```
*** Reminder: check the oven ***
```

* This command shows the background process by using `fork()` and `sleep()`.
* Parent retuns the prompt instantly and the child waits and prints the notification (the reminder user chooses)

## Testing:

The outputs that I've got while I've tested my implementations can be seen in the imgs folder. I tested different commands and got successful outputs.

## Repo link:

https://github.com/oozak23/COMP-304-Shell-ish-Spring-2026-Assignment-1-/tree/main


## Notes:

I've used several web and AI tools. They are cited below.

* www.stackoverflow.com: I've used this website for almost any question that I've had in mind.

* www.chatgpt.com / www.claude.ai: I've used ChatGPT and Claude AI for getting some general knowledge, tips, bug fixes.

* www.geeksforgeeks.org: I've used this website for understaning the concepts of piping, forking, redirecting etc.

* https://www.youtube.com/@CodeVault: I watched the vidoes about redirecting and pipes from this channel.

