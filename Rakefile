task :default => :new

require 'fileutils'

desc "create new post"
task :new do
  puts "please input the create post URL."
	@url = STDIN.gets.chomp
	puts "input post title"
	@name = STDIN.gets.chomp
	puts "input post subtitle"
	@subtitle = STDIN.gets.chomp
	puts "input post category, with blank to divide"
	@categories = STDIN.gets.chomp
	puts "input post tag"
	@tag = STDIN.gets.chomp
	@slug = "#{@url}"
	@slug = @slug.downcase.strip.gsub(' ', '-')
	@date = Time.now.strftime("%F")
	@post_name = "_posts/#{@date}-#{@slug}.md"
	if File.exist?(@post_name)
			abort("file exist! create fail!")
	end
	FileUtils.touch(@post_name)
	open(@post_name, 'a') do |file|
			file.puts "---"
			file.puts "layout: post"
			file.puts "title: #{@name}"
			file.puts "subtitle: #{@subtitle}"
			file.puts "author: pizida"
			file.puts "date: #{Time.now}"
			file.puts "categories: #{@categories}"
			file.puts "tag: #{@tag}"
			file.puts "---"
	end
	exec "vi #{@post_name}"
end
