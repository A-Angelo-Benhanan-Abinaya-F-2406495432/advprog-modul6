# Commit 1 Reflection Notes

In this milestone, I observed first-hand the request-response protocol of websites. By using TcpListener::bind("127.0.0.1:7878"), I'm able to listen for incoming TCP connections and show it's header (just the header because handle_connection() stops when it encounters an blank line and the request's header and body is separated by a blank line). Rust's ownership model ensures that the mutable stream in handle_connection() is properly managed, preventing accidental concurrent modifications.
