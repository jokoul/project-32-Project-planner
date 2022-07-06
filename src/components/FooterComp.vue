<template>
  <footer class="footer">
    <p>Project Planner, Copyright &copy; 2022 develop by Joan Kouloumba</p>
    <div>
      <ul class="social-media">
        <li>
          <a
            href="https://www.linkedin.com/in/joan-kouloumba-570a7680/"
            target="_blank"
            ><i class="fa-brands fa-linkedin-in"></i
          ></a>
        </li>
        <li>
          <a href="https://twitter.com/joanKouloumba" target="_blank"
            ><i class="fa-brands fa-twitter"></i
          ></a>
        </li>
        <li>
          <a href="https://github.com/jokoul" target="_blank"
            ><i class="fa-brands fa-github"></i
          ></a>
        </li>
      </ul>
      <p>
        <a
          href="https://joan-kouloumba.in/professional-site/index.html#achievements"
          >Visit more site like this on the professional site.</a
        >
      </p>
    </div>
  </footer>
</template>

<script>
export default {};
</script>

<style>
/*FOOTER STYLE */
.footer {
  height: 10rem;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: linear-gradient(#555, #555);
  background: -webkit-linear-gradient(#555, #555);
  background: -moz-linear-gradient(#555, #555);
  background: -o-linear-gradient(#555, #555);
  padding: 1rem;
  margin-top: 10rem;
}
.footer p {
  font-size: 1.2rem;
  color: #fff;
  text-align: center;
}
footer div {
  margin-left: 2rem;
}
.footer p a {
  text-decoration: none;
  color: #00ce89;
}
.footer p a:hover {
  text-decoration: underline;
  cursor: pointer;
}
.footer ul {
  display: flex;
  justify-content: space-around;
  align-items: center;
  color: #5d12e7;
  margin-bottom: 1rem;
}
.footer ul li a {
  color: #fff;
}
.footer ul li {
  transition: all 0.2s;
  list-style-type: none;
  text-align: center;
}
.footer ul li:hover {
  transform: scale(1.3);
}
@media screen and (max-width: 450px) {
  .footer {
    flex-direction: column-reverse;
  }
  footer div {
    margin-left: 0;
    margin-bottom: 2rem;
  }
}
</style>
