# Commit 1 Reflection Notes

In this milestone, I observed first-hand the request-response protocol of websites. By using TcpListener::bind("127.0.0.1:7878"), I'm able to listen for incoming TCP connections and show it's header (just the header because handle_connection() stops when it encounters an blank line and the request's header and body is separated by a blank line). Rust's ownership model ensures that the mutable stream in handle_connection() is properly managed, preventing accidental concurrent modifications.

# Commit 2 Reflection Notes

![Commit 2 screen capture](/assets/images/commit2.png)

In this milestone, I learned how to properly structure an HTTP response. It must include things such as status line, headers such as Content-Length, and followed by \r\n\r\n that creates a blank line, separating the header from the body. The body itself contains the HTML file hello.html that's loaded by fs::read_to_strin() and included into the response body.

# Commit 3 Reflection Notes

![Commit 3 screen capture](/assets/images/commit3.png)

In this milestone, I extended the server to read and validate the first line of the HTTP request. The split between response if done by using if-else and checking whether the request's first line is "GET / HTTP/1.1" and then giving the appropriate HTML page.

# Commit 4 Reflection Notes

In this milestone, I created a single-threaded server. When I hit /sleep in one tab, the other tab loading / is forced to wait until the first tab is done loading even though it has nothing to do with sleeping. It happens because the server processes connections one at a time using a for loop. As such, it must complete the current iteration before moving to the next one. If one iteration takes a long time, the others must wait for it. This can create huge problems, especially if many users send request at the same time. Response time would degrade quickly, not just for the slow requester. 