SRC = Dir.glob('*.sass').reject do |f|
  File.basename(f).match(/^_/)
end

CSS = SRC.map { |x| x[0...-4] + 'css' }

task :default => CSS

rule '.css' => ['.sass'] do |t|
  print "Generating #{t.name}... "
  File.open(t.name, 'w') do |f|
    f.puts "/* #{generated_at} */"
    f.puts
    f.puts %x{sass #{t.source}}
  end
  puts "OK"
end

desc "Clean up generated files."
task :clean do
  CSS.each { |x| rm_f x }
end

def generated_at
  "Generated at #{Time.now.strftime('%Y-%m-%d %H:%M:%S')} from #{File.basename(File.dirname(__FILE__))}@#{`hostname`.chomp} commit #{`git describe --always`.chomp}."
end
  