## This is a skeleton [Travis CI](http://travis-ci.org/) setup, for testing pure javascript projects (not node.js) with [jasmine](http://pivotal.github.com/jasmine/)  

#### Setup Locally
NOTE: This is not mandatory. Travis won't care if your local setup works.
```bash
git clone git@github.com:pwmckenna/travis_jasmine.git
cd travis_jasmine
bundle install
bundle exec rake
```
If this works, then you're probably safe to just do ```cp -R * YOUR_REPO_PATH``` and assume that once you've enabled travis on your repo, things will work.

#### Update files to reference your code  
Start by copying this entire project into the root of your project. You'll want to make sure to update the following files with your javascript file paths.  
__Note:__ Don't add your spec files here, just the javascript required by those tests...  
- *spec/javascripts/support/jasmine.yml*
```yml
src_files:
   - spec/javascripts/lib/jquery.js
   - spec/javascripts/lib/json2.js
   - spec/javascripts/lib/underscore.js
   - spec/javascripts/lib/backbone.js
   # ADD OTHER FILES HERE!
```
For instance, my [Backbrace](http://pwmckenna.github.com/backbrace/) project's *jasmine.yml* references the *backbrace.min.js* file as well  
```yml
src_files:
   - spec/javascripts/lib/jquery.js
   - spec/javascripts/lib/json2.js
   - spec/javascripts/lib/underscore.js
   - spec/javascripts/lib/backbone.js
   - backbrace.js
```

- *spec/SpecRunner.html*
You don't need to update this file to get everything working on Travis, but it'll allow you to run your unit tests in a browser, which can be occasionally useful. You just need to include your javascript files like you would with any other html file.  
```html
  <!-- include source files here... -->
  <script src="javascripts/lib/jquery.js"></script>
	<script src="javascripts/javascripts/lib/json2.js"></script>
	<script src="javascripts/lib/underscore.js"></script>
  <script src="javascripts/lib/backbone.js"></script>
  <!-- add your files here! -->
```

#### Great, you're ready to roll. Time to write tests!
This part is easy. Open up *spec/javascripts/specs/sample_spec.js* and flesh out those Jasmine tests. Feel free to add additional spec files in this directory. They will be run automatically for you.  
```js
(function() {
    describe('Tests', function() {
      it('tests stuff with jasmine', function() {
        expect(true).toBeTruthy();
      });
    });
}).call(this);
```

#### Setup Travis
You can either [log into travis](http://travis-ci.org/profile) and set up your repo via the toggle, or follow the [how-to](http://about.travis-ci.org/docs/user/how-to-setup-and-trigger-the-hook-manually/) to do it manually.  
  
Once you've done that, you can add the travis-ci build status icon to your readme. The link looks like the following:  
https://secure.travis-ci.org/username/repository.png  
<br>
When you're done, hopefully you'll have one of these to show off.  
![travis](https://secure.travis-ci.org/pwmckenna/travis_jasmine.png)  

### Good Luck!  