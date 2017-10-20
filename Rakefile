require 'YAML'

task :default do
  puts 'you have no default task'
end

task :new, [:post_name] do |task, args|
  # create post filename
  time_stamp = Time.now.strftime("%Y-%m-%d")
  title = args[:post_name].tr(' ', '-')
  file_name = "#{time_stamp}-#{title}.md"
  
  # create front matter
  front_matter = YAML.load_file('./_data/front_matter_template.yml')
  front_matter["date"] = Date.parse(time_stamp)
  front_matter["title"] = args[:post_name]
  front_matter_formatted = front_matter.to_yaml + "---\n"

  # write file
  File.write("_posts/#{file_name}", front_matter_formatted)

  # open for editing
  system("subl _posts/#{file_name}")
end

task :build do
  system("jekyll build")
end

task :push do 
  system("git add . && git commit -m 'rake deploy commit' && git push origin master")  
end

task :deploy => [:build, :push] do
  system("./bin/deploy")
end

