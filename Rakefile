task default: :cson

csons = []
errors = []

Dir.glob('index/**/*.cson') { |c| csons << c.sub(/\.cson$/, '.json') }

csons = csons.sort

task :cson => csons


rule '.json' => '.cson' do |csontojson|
  sh "cson2json #{csontojson.source} >| #{csontojson.name}" do |o, r|
    errors << "Error on #{t.name}: #{r}" if ! o
  end
end

