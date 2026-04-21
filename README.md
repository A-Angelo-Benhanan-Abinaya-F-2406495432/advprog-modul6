# Commit 1 Reflection Notes

In this milestone, I observed first-hand the request-response protocol of websites. By using TcpListener::bind("127.0.0.1:7878"), I'm able to listen for incoming TCP connections and show it's header (just the header because handle_connection() stops when it encounters an blank line and the request's header and body is separated by a blank line). Rust's ownership model ensures that the mutable stream in handle_connection() is properly managed, preventing accidental concurrent modifications.

# Commit 2 Reflection Notes

![Commit 2 screen capture](/assets/images/commit2.png)

In this milestone, I learned how to properly structure an HTTP response. It must include things such as status line, headers such as Content-Length, and followed by \r\n\r\n that creates a blank line, separating the header from the body. The body itself contains the HTML file hello.html that's loaded by fs::read_to_strin() and included into the response body.