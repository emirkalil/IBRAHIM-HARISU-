
const express = require("express");
const mongoose = require("mongoose");
const dotenv = require("dotenv");

dotenv.config();

const app = express();
app.use(express.json());

app.use("/api/auth", require("./routes/auth"));
app.use("/api/wallet", require("./routes/wallet"));
app.use("/api/payment", require("./routes/payment"));

mongoose.connect(process.env.MONGO_URI)
  .then(() => console.log("DB connected"))
  .catch(err => console.log(err));

app.listen(5000, () => console.log("Server running"));