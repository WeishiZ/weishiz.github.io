javascript
variable is lexical scope,
but the value is dynamically bind




start(done);


getServer();

=======

let serverInstance;


exports.start = function(cb) {
  db.connectDB(function() {
    //exports.serverInstance =
    serverInstance = http.createServer(app);
    serverInstance.listen(port, function() {
      console.log(TAG + "Listening to port: " + port);
       cb && cb();
    });
  });
}

exports.shutdown = function(cb) {
  console.log(TAG + "Shutting down service...");
  db.closeDB(function() {
    if (serverInstance) {
      serverInstance.close(cb);
    }
  });
}

exports.getServer = function() {
  return serverInstance;
};

vs.
exports.getServer = serverInstance;
