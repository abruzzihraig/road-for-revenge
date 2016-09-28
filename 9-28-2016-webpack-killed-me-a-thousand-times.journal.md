### Webpack Killed Me A Thousand Times
I’ve been using Webpack more than half year. It hurts me every time when I want to implement some essential features. I was totally confused why there are so many people like its black magic with its shitty documents?

Whatever I complain, I have to say there are some features under the hood of Webpack are actually useful and effective for developing. But these two days, I met some issues with build flow based on Webpack, and that make my tasks on KDP project are delayed.

I have two projects, one named KDP, another named Kanvas. The project Kanvas is an image editor could be released as a standalone version or an embedded version to KDP.

And we use AWS S3 as a static server. So each of those projects will be deployed to different S3 buckets. However, the AWS S3 doesn’t support compression automatically like a real HTTP server, a Nginx server for instance. But we still could compress or make cache metadata for some kinds of files before we upload them.

So the trouble comes:
1. I need compiled and compressed resources from Kanvas to a S3 bucket as a standalone version.
2. I need compiled but uncompressed resources from Kanvas to KDP, to make developers could use Kanvas within KDP development mode. In this integration version of Kanvas, it need to import two scripts for initialising and controlling Kanvas from outside. The both scripts shouldn’t be compressed or with a hash.
3. I need compiled and compressed resources from KDP to another S3 bucket, it should be a public website for our clients. Since Kanvas and KDP are different projects, they have individual Webpack flow for themselves. So the process of compressing KDP doesn’t include the code from Kanvas. That means I have to compress code in Kanvas first, then copy the part-compressed code to KDP compiled folder.

However, it’s not over yet. When I upload the final compiled folder to S3 bucket, I used a loader to add different HTTP metadata for each file will be uploaded. That means I have to ignore some files to prevent adding wrong metadata on.

The whole build flow made me hurt before, it always take me much time, and the logic order is hard to remember. Once I made a mistake during the flow, I have to take 5 or 10 minutes to rebuild them again.

So I refacted the whole build flow, I made three different environments for KDP, it includes ‘dev’, ‘dist’, ‘s3’. And I made four different environments for Kanvas, they are ‘dev’, ‘dist’, ‘gzip’, and ’s3’.

Some of those environments have different basic configs are extended to the main Webpack config, especially some different paths. At the mean time, I made our API configs relating to these different environments.

And I also wrote my AWS keys to the environment of my computer, then I could use them when deploy. Except some npm scripts on the both projects, I also wrote some alias scripts on my ZShell to make the complex building logic simpler.

So even though I met lots of pits in Webpack again, finally I got only two commands to handle all those shitty work. And yes, I’m free again.
